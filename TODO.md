# Phân chia nhiệm vụ  
## Project: Traffic Sign Recognition Realtime bằng YOLOv8

| Thành viên | File có thể đụng vào | Nhiệm vụ | Input cần sử dụng | Output yêu cầu |
|---|---|---|---|---|
| Thành viên 1 | `dataset/`, `data.yaml`, `classes.txt`, `image_preprocess.py` | Chuẩn bị dataset YOLO, convert annotation sang format YOLO, resize ảnh, augment dữ liệu, chia train/val/test | Dataset GTSRB hoặc ảnh biển báo thu thập thêm | Dataset đúng format YOLO gồm `images/`, `labels/`, `data.yaml` |
| Thành viên 2 | `train.py`, `evaluate.py`, `models/`, `runs/train/` | Train YOLOv8, tuning `epoch`, `batch size`, `imgsz`, evaluate model, lưu weight tốt nhất | Dataset đã chuẩn hóa từ thành viên 1 | File `best.pt`, accuracy/mAP, confusion matrix, biểu đồ loss |
| Thành viên 3 | `camera_handler.py`, `inference.py`, `detector.py`, `confidence_filter.py` | Xây dựng realtime detection bằng webcam, xử lý inference YOLO, lọc confidence thấp | Webcam frame + model `best.pt` | Hệ thống detect realtime trả bbox + class + confidence |
| Thành viên 4 | `overlay_ui.py`, `draw_box.py`, `fps_counter.py`, `config.py` | Thiết kế giao diện realtime, vẽ bounding box, hiển thị FPS, cảnh báo biển báo nguy hiểm | Frame + kết quả detect từ YOLO | Video realtime có FPS, label, màu bbox, cảnh báo |
| Thành viên 5 | `main.py`, `logger.py`, `file_utils.py`, `README.md`, `requirements.txt` | Tích hợp toàn bộ hệ thống, test lỗi, logging, quản lý config, viết tài liệu hướng dẫn sử dụng | Toàn bộ module từ các thành viên khác | Chương trình chạy hoàn chỉnh + tài liệu hướng dẫn |