Project Description
1. Dataset

Dataset được sử dụng trong dự án là Pascal VOC (hoặc dataset bạn đang dùng).

Bao gồm các ảnh và annotation cho bài toán object detection
Annotation được lưu dưới dạng:
XML (VOC format) hoặc COCO JSON (nếu bạn convert)
Mỗi ảnh chứa:
Bounding box (tọa độ vật thể)
Label (class)

📂 Cấu trúc dữ liệu
data/
│── images/

│── annotations/

│── train.txt / val.txt
2. Preprocessing

Các bước tiền xử lý dữ liệu trước khi đưa vào model:

Resize ảnh về kích thước phù hợp (ví dụ: 320 hoặc 640)
Normalize ảnh theo chuẩn ImageNet:
mean = [0.485, 0.456, 0.406]
std  = [0.229, 0.224, 0.225]
//  bước này không cần vì model load lên đã được Normalize sẵn //
3. Model

Mô hình sử dụng:

👉 Faster R-CNN với backbone MobileNetV3

🧠 Kiến trúc:
Backbone: MobileNetV3 (lightweight)
Feature Pyramid Network (FPN)
Region Proposal Network (RPN)
ROI Head:
Classification
Bounding box regression
⚙️ Tùy chỉnh:
model = fasterrcnn_mobilenet_v3_large_320_fpn()
model.roi_heads.box_predictor = FastRCNNPredictor(
    in_channels, num_classes
)
4. Training
⚙️ Thông số:
Optimizer: SGD
Learning rate: 0.001
Momentum: 0.9
Batch size: 8
Epochs: 10
📈 Logging:
Sử dụng TensorBoard:
runs/exp1/

💾 Checkpoint:
Lưu model tốt nhất:
checkpoint/best_model.pt

5. Evaluation
Metric chính: mAP (mean Average Precision)
Theo dõi:
Loss
mAP qua từng epoch
