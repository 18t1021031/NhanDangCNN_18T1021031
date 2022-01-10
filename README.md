#Source code Nhận dạng khuôn mặt bằng phương pháp mạng nơron tích chập (CNN)

Họ và tên: Nguyễn Thành Dẫn
Mã sinh viên: 18T1021031

Bước 1: Tạo và tải các thứ cần thiết
  Tạo thư mục Dataset trong NhanDangCNN_18T1021031, trong đó tạo tiếp thư mục FaceData và dưới FaceData là tạo tiếp 2 thư mục raw và processed.
  Tạo thư mục Models trong NhanDangCNN_18T1021031 để chờ sẵn tẹo lưu model InceptionResnetV1.
  Download model InceptionResnetV1.
    https://miai.vn/download.php?url=https://drive.google.com/file/d/1EXPBSXwTaqrSC0OhUdXNmKSh9qJUQ55-/view
  chú ý chỉ lấy file (không có file facemodel.pkl) vỏ vào thư mục Models ở trên
Bước 2:
  Sưu tầm ảnh của 2 người trở lên, mỗi người 10 tấm hình rõ mặt. Mình ví dụ 2 người tên là NguyenVanA và LeThiB. Tạo 2 thư mục NguyenVanA và LeThiB trong thư mục raw và copy ảnh của 2 người vào riêng 2 thư mục đó, ảnh của ai vào thư mục của người đó.
  Từ thư mục NhanDangCNN_18T1021031
        pip install -r requirements.txt //Tải các thư viện
        python src/align_dataset_mtcnn.py  Dataset/FaceData/raw Dataset/FaceData/processed --image_size 160 --margin 32  --random_order --gpu_memory_fraction 0.25// Tiền xử lý
Bước 3:
        python src/classifier.py TRAIN Dataset/FaceData/processed Models/20180402-114759.pb Models/facemodel.pkl --batch_size 1000 //Huấn luyện
Bước 4:
        python src/face_rec_cam.py //Nhận dạng
