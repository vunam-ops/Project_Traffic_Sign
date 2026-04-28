# Project_Traffic_Sign
AI
🚦 Dự án: Nhận diện Biển báo Giao thông Việt Nam (6 Nhóm)Dự án này sử dụng mô hình YOLOv8/v11 để nhận diện và phân loại các nhóm biển báo giao thông tại Việt Nam. Toàn bộ quy trình từ gán nhãn đến huấn luyện được thực hiện trên Roboflow và Google Colab.

https://app.roboflow.com/join/eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3b3Jrc3BhY2VJZCI6IlpjMDBOM3hIZEpYd3hBNTlZbktWVlhSNzJnRDIiLCJyb2xlIjoib3duZXIiLCJpbnZpdGVyIjoidnVoYW5hbTMwMDUyMDA0QGdtYWlsLmNvbSIsImlhdCI6MTc3NzM2MDI3MX0.4Hp1F_WCbCIOStjtoh1PxYqfy4TXtGDp7AfYvEEQ6vA

📂 Cấu trúc thư mục (GitHub)Các thành viên tuân thủ cấu trúc sau khi đẩy code lên:
PlaintextProject_Traffic_Sign/
├── notebooks/
│   └── train_yolo.ipynb    # File chạy chính trên Google Colab
├── media/                  # Video/Ảnh thực tế để test sau khi train
├── docs/                   # Tài liệu báo cáo, sơ đồ thuật toán
├── README.md               # File hướng dẫn này
└── requirements.txt        # Danh sách thư viện cần cài (ultralytics, opencv...)
🛠 Quy trình làm việc (Workflow)
1. Quản lý dữ liệu (Roboflow)Link Workspace: 
Danh sách 6 nhãn (Labels):
  prohibitory: Biển báo cấm.
  danger: Biển báo nguy hiểm.
  mandatory: Biển hiệu lệnh.
  informational: Biển chỉ dẫn.
  supplemental: Biển phụ.
  unclear: Biển mờ, không rõ loại.
Lưu ý gán nhãn: Vẽ khung (Bounding Box) sát mép biển báo, không để dư quá nhiều nền.
2. Huấn luyện mô hình (Google Colab)
Sử dụng file notebooks/train_yolo.ipynb.
Kết nối với Roboflow qua API Key để tải dữ liệu (không tải thủ công).
Sử dụng GPU (T4) để huấn luyện.
Mục tiêu: Đạt mAP@0.5 trên 85%.3. 
3. Lưu trữ kết quả
Sau khi huấn luyện, file trọng số tốt nhất là best.pt.
Cần lưu file này vào thư mục cá nhân hoặc Drive chung của nhóm để sử dụng cho bước nhận diện thực tế.

🚀 Hướng dẫn cài đặt cho thành viên mới
Để chạy thử code của nhóm trên máy cá nhân, hãy thực hiện các lệnh sau:
1. Clone project:
Bash
git clone https://github.com/[user-name]/Project_Traffic_Sign.git
2. Cài đặt thư viện:
Bash
pip install -r requirements.txt
pip install ultralytics
3. Chạy thử mô hình (Inference):
Python
from ultralytics import YOLO
model = YOLO('path/to/best.pt')
results = model.predict(source='media/test_image.jpg', save=True)
⚠️ Lưu ý quan trọngCommit code: Trước khi git push, hãy đảm bảo code đã chạy được trên Colab và không chứa thông tin cá nhân (như API Key của Roboflow - hãy dùng biến ẩn).Augmentation: Chỉ thực hiện bước này sau khi đã gán nhãn xong ít nhất 90% dữ liệu gốc.Đồng bộ: Nếu ai thay đổi tên nhãn trên Roboflow, phải thông báo ngay cho cả nhóm để cập nhật file data.yaml.
Chúc nhóm hoàn thành đồ án xuất sắc! 🚀