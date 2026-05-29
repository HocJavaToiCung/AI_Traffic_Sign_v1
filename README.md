# AI_Traffic_Sign_v1
 # Traffic Sign Recognition Project - Task Checklist

## Core Features
- [X] Create rules
- [ ] Thiết lập luồng đọc Camera Realtime với YOLO và tối ưu FPS.
- [ ] Xây dựng bộ tiền xử lý hình ảnh (Preprocessing Pipeline).
- [ ] Tích hợp mô hình YOLOv8 để Detect vùng chứa biển báo (Bounding box).
- [ ] Tích hợp Custom CNN để Classify chính xác loại biển báo.
- [ ] Viết module log lỗi và xuất báo cáo FPS hệ thống.

## Tối ưu & Mở rộng
- [ ] Áp dụng Threading để tách biệt luồng Cam và luồng Inference.
- [ ] Phát âm thanh cảnh báo (Text-to-Speech) khi phát hiện biển báo nguy hiểm.

## Structure of Project 
# Structure of Project

```text
traffic-sign-AI/
│
├── dataset/
│   ├── images/
│   │   ├── train/                # Training images
│   │   ├── val/                  # Validation images
│   │   └── test/                 # Testing images
│   │
│   ├── labels/
│   │   ├── train/                # YOLO labels for training
│   │   ├── val/                  # YOLO labels for validation
│   │   └── test/                 # YOLO labels for testing
│   │
│   ├── classes.txt               # List of traffic sign classes
│   └── data.yaml                 # YOLO dataset configuration
│
├── models/
│   ├── yolov8n.pt                # Pretrained YOLOv8 nano model
│   ├── best.pt                   # Best trained model weights
│   └── last.pt                   # Latest training checkpoint
│
├── configs/
│   ├── config.py                 # Main project configuration
│   └── camera_config.py          # Camera settings configuration
│
├── src/
│   ├── camera/
│   │   └── camera_handler.py     # Webcam/video stream handler
│   │
│   ├── detection/
│   │   ├── detector.py           # YOLO detection logic
│   │   ├── inference.py          # Prediction pipeline
│   │   └── confidence_filter.py  # Filter low-confidence detections
│   │
│   ├── preprocessing/
│   │   ├── image_preprocess.py   # Image preprocessing functions
│   │   └── roi_crop.py           # Region of Interest cropping
│   │
│   ├── ui/
│   │   ├── overlay_ui.py         # Display UI overlay
│   │   ├── draw_box.py           # Draw bounding boxes
│   │   └── fps_counter.py        # FPS display utility
│   │
│   ├── training/
│   │   ├── train.py              # YOLO training script
│   │   ├── evaluate.py           # Model evaluation script
│   │   └── export_model.py       # Export trained model
│   │
│   ├── utils/
│   │   ├── logger.py             # Logging utility
│   │   ├── file_utils.py         # File handling utility
│   │   └── class_mapping.py      # Class ID ↔ class name mapping
│   │
│   └── main.py                   # Main application entry point
│
├── notebooks/
│   └── experiment.ipynb          # Jupyter notebook experiments
│
├── runs/
│   ├── detect/                   # Detection output results
│   └── train/                    # Training result logs
│
├── requirements.txt              # Python dependencies
├── README.md                     # Project documentation
└── .gitignore                    # Git ignored files

ffff
