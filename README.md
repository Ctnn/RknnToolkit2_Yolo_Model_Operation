# RknnToolkit2_Yolo_Model_Operation


STEPS FOR MODEL TRANSLATION

STEP -1- 
Clone Yolov5 repository: https://github.com/ultralytics/yolov5

STEP -2-
NOTE1: "If you have a .pth model, you need to convert this model to .pt model"

First we need to convert the .pt model to onnx.
Run the following terminal code inside the Yolov5 folder (best.pt model to be translated)
NOTE2: Opset must be 12 !!!

yolov5>python export.py --weights models/best.pt --img 640 --batch 1 --include onnx --opset 12

STEP -3-

Inside the onnx_to_rknn.py file in the repository;
- input model (.onnx)
- output model (.rknn)
- classes name
- IMG_PATH
- DATASET (we must specify the location of the test images as .txt extension)
IMPORTANT : Onnx model will be analyzed via netron and will have 3 outputs before post-processing (ReShape), the output paths of this place are taken and
 The variables must be updated via the ret variable.
"output1",
"output2",
"output3"

By updating these parameters you can get the .rknn model output.
