# Vision

- <img width="602" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/238e031a-f219-45a7-8c9d-23acf7733df6">
- <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/3a90d2f1-591e-4c7f-950a-e06b575a9058">

# Barcode

- <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/b6b2405d-78c0-47cd-8885-20bf58ba46e8">
- <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/0588fd05-5cbd-4d6b-94cc-516db00f3773">
  - ROI注目画像領域を指定しなかった場合、境界ボックスの位置は画像全体を基準に算出される
  - ROIを指定した場合は、画像の中心部だけに集中するよう指示される
  - Revision２では、境界ボックスが他のVision仕様と同じようROI基準で算出される
- <img width="624" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/2a3fea8b-6581-4c46-a270-09463e8692fa">
  - 何度もスキャンする必要がない

# 読み取りプロセス

- <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/5a53cd77-1c20-4162-a12b-590cea9cf322">
  - 一つのコードが何度も検出されてしまうので、バーコードをデコードしたデータが格納されるペイロードを参照して、重複を排除する
- <img width="627" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/f45c92c6-09e0-40e0-bee1-4b74e5a46f30">

# Text

- <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/2486e7ef-d902-43e0-8a38-378b43cc9754">
- <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/1bc478a4-4262-4a5b-9a3e-685ed0d884fa">

# Document

- <img width="628" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/92054035-2f9c-4feb-b4a4-138090637121">
- <img width="626" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/269dac4a-f817-453e-b11a-18be81c13a1b">
- <img width="625" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/f2a1ce69-7978-4dee-9e68-8b809be229bb">
- <img width="638" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/801c86ec-ec96-4d59-bfbf-6c545199bf1c">
- <img width="640" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/fc252749-34ef-4001-81cb-856910a23277">
- <img width="639" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/56db65c6-bd38-4ae7-b48a-fb907063277f">
- <img width="635" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/0306448b-e5ef-418e-a842-c1b48a45583f">
- <img width="639" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/dea6b225-2bd3-4ce1-9c6c-df52ce6f0203">
- <img width="638" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/5565ae6c-23ab-425a-882e-89b5900ea5b6">
- <img width="637" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/2ebfb18a-1520-45d1-a1eb-ec72bff4424a">
- <img width="640" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/cf80c810-3b11-4c36-abaa-f5292cb9f778">
- <img width="636" alt="image" src="https://github.com/chocoyama/WWDC/assets/7239831/376e1808-c8b3-4af2-832a-138d88967320">

```swift
import Foundation
import CoreImage
import Vision
import CoreML

guard var inputImage = CIImage(contentsOf: #fileLiteral(resourceName: "IMG_0001.HEIC"))
else { fatalError("image not found") }

inputImage

let requestHandler = VNImageRequestHandler(ciImage: inputImage)
let documentDetectionRequest = VNDetectDocumentSegmentationRequest()
try requestHandler.perform([documentDetectionRequest])

guard let document = documentDetectionRequest.results?.first,
      let documentImage = perspectiveCorrectedImage(from: inputImage, rectangleObservation: document) else {
          fatalError("Unable to get document image.")
      }
    
documentImage
let documentRequestHandler = VNImageRequestHandler(ciImage: documentImage)

/*
 TODO
  Detect barcodes
  Detect rectangles
  Recognize text
  Perform those requests
  Scan checkboxes
 */

var documentTitle = "Don't know yet"

let barcodesDetection = VNDetectBarcodesRequest() { request, _ in
    guard let result = request.results?.first as? VNBarcodeObservation,
          let payload = result.payloadStringValue else { return }
    documentTitle = "\(payload) was: "
}
barcodesDetection.symbologies = [.qr]

var checkBoxImages: [CIImage] = []
var rectangles: [VNRectangleObservation] = []

let rectanglesDetection = VNDetectRectanglesRequest { request, error in
    rectangles = request.results as! [VNRectangleObservation]
    // sort by vertical coordinates
    rectangles.sort{$0.boundingBox.origin.y > $1.boundingBox.origin.y}
    
    for rectangle in rectangles {
        guard let checkBoxImage = perspectiveCorrectedImage(from: documentImage, rectangleObservation: rectangle)
        else { print("Could not extract document"); return }
        checkBoxImages.append(checkBoxImage)
    }
}
rectanglesDetection.minimumSize = 0.1
rectanglesDetection.maximumObservations = 0

var textBlocks: [VNRecognizedTextObservation] = []

let ocrRequest = VNRecognizeTextRequest { request, error in
    textBlocks = request.results as! [VNRecognizedTextObservation]
}

do {
    try documentRequestHandler.perform([ocrRequest, rectanglesDetection, barcodesDetection])
} catch {
    print(error)
}


let classificationRequest = createclassificationRequest()

var index = 0
for checkBoxImage in checkBoxImages {
    let checkBoxRequestHandler = VNImageRequestHandler(ciImage: checkBoxImage)
    do {
        try checkBoxRequestHandler.perform([classificationRequest])
        if let classifications = classificationRequest.results as? [VNClassificationObservation] {
            if let topClassification = classifications.first
            {
                if topClassification.identifier == "Yes" && topClassification.confidence >= 0.9 {
                    for currentText in textBlocks {
                        if observationLinesUp(rectangles[index], with: currentText) {
                            let foundTextObservation = currentText.topCandidates(1)
                            documentTitle += foundTextObservation.first!.string + " "
                        }
                    }
                }
            }
        }
    } catch {
        print(error)
    }
    index += 1
}

print(documentTitle)



extension CGPoint {
    func scaled(to size: CGSize) -> CGPoint {
        return CGPoint(x: self.x * size.width, y: self.y * size.height)
    }
}
extension CGRect {
    func scaled(to size: CGSize) -> CGRect {
        return CGRect(
            x: self.origin.x * size.width,
            y: self.origin.y * size.height,
            width: self.size.width * size.width,
            height: self.size.height * size.height
        )
    }
}

public func observationLinesUp(_ observation: VNRectangleObservation, with textObservation: VNRecognizedTextObservation ) -> Bool {
    // calculate center
    let midPoint =  CGPoint(x:textObservation.boundingBox.midX, y:observation.boundingBox.midY)
    return textObservation.boundingBox.contains(midPoint)
}

public func perspectiveCorrectedImage(from inputImage: CIImage, rectangleObservation: VNRectangleObservation ) -> CIImage? {
    let imageSize = inputImage.extent.size
    
    // Verify detected rectangle is valid.
    let boundingBox = rectangleObservation.boundingBox.scaled(to: imageSize)
    guard inputImage.extent.contains(boundingBox)
    else { print("invalid detected rectangle"); return nil}
    
    // Rectify the detected image and reduce it to inverted grayscale for applying model.
    let topLeft = rectangleObservation.topLeft.scaled(to: imageSize)
    let topRight = rectangleObservation.topRight.scaled(to: imageSize)
    let bottomLeft = rectangleObservation.bottomLeft.scaled(to: imageSize)
    let bottomRight = rectangleObservation.bottomRight.scaled(to: imageSize)
    let correctedImage = inputImage
        .cropped(to: boundingBox)
        .applyingFilter("CIPerspectiveCorrection", parameters: [
            "inputTopLeft": CIVector(cgPoint: topLeft),
            "inputTopRight": CIVector(cgPoint: topRight),
            "inputBottomLeft": CIVector(cgPoint: bottomLeft),
            "inputBottomRight": CIVector(cgPoint: bottomRight)
        ])
    return correctedImage
}

public func createclassificationRequest() -> VNCoreMLRequest
{
    let classificationRequest: VNCoreMLRequest = {
        // Load the ML model through its generated class and create a Vision request for it.
        do {
            let coreMLModel = try MLModel(contentsOf: #fileLiteral(resourceName: "CheckboxClassifier.mlmodelc"))
            let model = try VNCoreMLModel(for: coreMLModel)
            
            return VNCoreMLRequest(model: model)
        } catch {
            fatalError("can't load Vision ML model: \(error)")
        }
    }()
    return classificationRequest
}
```
