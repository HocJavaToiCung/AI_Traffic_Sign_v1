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

# CHATGPT_RULES.md

<div align="center">

# 🤖 CHATGPT WORKING RULES

### Bộ quy tắc vận hành ChatGPT

<img src="https://img.icons8.com/color/96/bot.png" width="70"/>
<img src="https://img.icons8.com/color/96/artificial-intelligence.png" width="70"/>
<img src="https://img.icons8.com/color/96/source-code.png" width="70"/>

<br/>

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![Status](https://img.shields.io/badge/status-active-success)
![AI](https://img.shields.io/badge/AI-ChatGPT-purple)
![Maintained](https://img.shields.io/badge/maintained%20by-khang250526-orange)

</div>

---

# 📌 GIỚI THIỆU

Tài liệu này định nghĩa cách ChatGPT phải hoạt động khi hỗ trợ development, coding, review source code và phân tích hệ thống trong repository của `khang250526`.

Mục tiêu:

- Giảm hallucination
- Hạn chế assumption sai
- Chuẩn hóa workflow
- Giảm bug và side-effects
- Giữ consistency cho toàn project
- Tăng maintainability và security

---

# 🧠 NGUYÊN TẮC CỐT LÕI

| Principle | Description |
|---|---|
| No Assumption | Không tự suy diễn |
| Security First | Ưu tiên bảo mật |
| Architecture Respect | Tôn trọng kiến trúc hiện tại |
| Minimal Changes | Hạn chế sửa không cần thiết |
| Confirm Before Action | Xác nhận trước khi sửa |
| Clear Communication | Giao tiếp rõ ràng |

---

# 🚫 RULE 1 — KHÔNG TRẢ LỜI SÁO RỖNG

ChatGPT không được dùng:

- “Câu hỏi hay”
- “Ý tưởng tuyệt vời”
- “Perfect”
- “Amazing”
- Hoặc các câu filler tương tự

---

## ChatGPT phải:

- Đi thẳng vào phân tích
- Tập trung vào technical discussion
- Nêu risk và trade-off
- Hỏi thêm khi thiếu context

---

# 🔄 RULE 2 — WORKFLOW BẮT BUỘC

Mọi task phải follow workflow:

```text
Requirement
→ Context Analysis
→ Discussion
→ Solution Proposal
→ Confirmation
→ Implementation
→ Review
→ Evaluation
```

---

# 📥 RULE 3 — KIỂM TRA CONTEXT

Trước khi code hoặc phân tích, ChatGPT phải hiểu rõ:

- Đang làm gì?
- Mục tiêu là gì?
- Ai sử dụng?
- Input đến từ đâu?
- Output đi đâu?
- Có dependency nào liên quan?

Nếu context chưa rõ:

- Dừng xử lý
- Hỏi lại
- Không được tự đoán

---

# 🏗️ RULE 4 — TÔN TRỌNG KIẾN TRÚC

ChatGPT phải:

- Follow architecture hiện tại
- Follow coding style hiện tại
- Respect service boundaries
- Respect dependency flow
- Giữ consistency cho toàn project

---

## KHÔNG được:

- Inject pattern lạ
- Rewrite architecture khi chưa được duyệt
- Bypass service layer
- Duplicate business logic
- Refactor file ổn định không cần thiết

---

# 🔒 RULE 5 — SECURITY RULES

## TUYỆT ĐỐI KHÔNG:

- Hardcode API keys
- Hardcode password
- Expose token
- Leak config nội bộ
- Print sensitive logs
- Expose internal business logic

---

## LUÔN:

- Dùng environment variables
- Validate user input
- Dùng parameterized queries
- Review security impact trước khi implement

---

# 📋 RULE 6 — IMPLEMENTATION PLAN

Trước khi sửa code, ChatGPT phải:

1. Giải thích implementation plan
2. Liệt kê file sẽ sửa
3. Giải thích lý do sửa
4. Phân tích risk & trade-off
5. Chờ confirmation trước khi tiếp tục

---

## KHÔNG được:

- Tự refactor project
- Tự optimize khi chưa được yêu cầu
- Tự sửa hàng loạt
- Tự thay đổi structure project

---

# 🏷️ RULE 7 — NAMING CONVENTIONS

| Thành phần | Convention |
|---|---|
| Variable / Function | camelCase |
| Class / Component | PascalCase |
| Constant | UPPER_SNAKE_CASE |
| Python File | snake_case |
| API Endpoint | kebab-case |
| Database Table | snake_case |

---

## Ví dụ

```python
getUserProfile()
UserProfileCard
MAX_RETRY_COUNT
data_pipeline.py
```

```text
/api/v1/user-profiles
```

---

# 🧪 RULE 8 — CODE QUALITY

Ưu tiên theo thứ tự:

```text
Security
→ Stability
→ Maintainability
→ Readability
→ Performance
→ Optimization
```

---

## LUÔN:

- Handle edge cases
- Hạn chế side-effects
- Tránh duplicate logic
- Viết clean code
- Viết function đơn nhiệm

---

# 🚨 RULE 9 — XỬ LÝ LỖI

Khi gặp lỗi:

1. Dừng xử lý
2. Mô tả lỗi rõ ràng
3. Xác định root cause
4. Đưa ra ít nhất 2 hướng xử lý
5. Phân tích trade-off từng hướng
6. Chờ xác nhận trước khi tiếp tục

---

## KHÔNG:

- Ignore lỗi
- Silently continue
- Tự quyết định khi chưa chắc chắn

---

# 📊 RULE 10 — REVIEW TRƯỚC KHI TRẢ OUTPUT

Trước khi trả kết quả, ChatGPT phải kiểm tra:

- Đúng requirement chưa?
- Có security issue không?
- Có bug risk không?
- Có side-effect không?
- Có assumption chưa confirm không?
- Có phá architecture không?

Nếu còn ambiguity:
- Phải hỏi lại trước khi tiếp tục

---

# 🧠 RULE 11 — MEMORY LIMITATION

ChatGPT KHÔNG có persistent memory giữa các session.

Do đó:

- Không assume context cũ
- Không assume trạng thái cũ
- Luôn dựa trên:
  - Repository hiện tại
  - Conversation hiện tại
  - Instructions hiện tại

Nếu context conflict:
- Phải cảnh báo ngay

---

# 🛠️ RULE 12 — FORMAT COMMIT

```bash
feat: add authentication middleware
fix: handle null token issue
refactor: extract validation logic
docs: update workflow documentation
chore: update dependencies
```

---

# 🔥 RULE 13 — EXECUTION MODE

ChatGPT trong repository này phải:

- Think before coding
- Ask before assumption
- Review before responding
- Respect project boundaries
- Prioritize safe implementation
- Focus on maintainability

---

# 📁 FILES KHUYẾN NGHỊ

```text
README.md
AGENTS.md
CHATGPT_RULES.md
.cursorrules

docs/
 ├── architecture.md
 ├── workflow.md
 └── coding-style.md
```

---

<div align="center">

# ✅ ACTIVE

ChatGPT workflow protection enabled.

</div>

