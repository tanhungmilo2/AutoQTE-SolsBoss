# Hướng dẫn cài tool trên máy khác (độ phân giải / scale khác)

Vì máy bạn (1920x1200, scale 125%) khác máy chủ (1920x1080, scale 100%),
**không thể** copy y nguyên `slot1_w.png`, `slot1_a.png`, `slot1_s.png`,
`slot1_d.png` và `rois.json` sang dùng — chữ W/A/S/D trong game sẽ hiện
với kích thước pixel khác trên màn hình bạn, nên các ảnh mẫu (template)
cũ sẽ không khớp nữa.

Làm theo đúng thứ tự bên dưới, chỉ mất khoảng 2 phút:

## Bước 1 — Cài thư viện
```
python -m venv .venv
.\.venv\Scripts\activate
pip install -r requirements.txt
```

## Bước 2 — Tạo template CHO RIÊNG MÁY BẠN
Mở game, chạy:
```
python generate_templates.py
```
- Di chuyển chuột vào **chính giữa** chữ W trong game → bấm phím `1`
- Chính giữa chữ A → bấm `2`
- Chính giữa chữ S → bấm `3`
- Chính giữa chữ D → bấm `4`

Xong sẽ có 4 file `w.png`, `a.png`, `s.png`, `d.png` trong thư mục.
Đổi tên (hoặc copy) 4 file này thành `slot1_w.png`, `slot1_a.png`,
`slot1_s.png`, `slot1_d.png` — ghi đè lên file cũ trong repo.

## Bước 3 — Calibrate ROI CHO RIÊNG MÁY BẠN
```
python main.py --calibrate
```
- Hover chuột vào giữa slot 1 → bấm `1`, slot 2 → bấm `2`... đến slot 5
- Xong sẽ tự lưu ra `rois.json` mới

## Bước 4 — Kiểm tra trước khi chạy thật
```
python diagnose_v2.py
```
File này show song song ảnh chụp thật vs template, giúp thấy ngay nếu
còn lệch/sai trước khi bấm phím thật trong lúc chơi.

## Bước 5 — Chạy tool
```
python main.py
```
Bấm phím `E` (hotkey mặc định) để trigger nhận diện.

---
### Nếu vẫn không nhận được (score thấp/`[unknown]`)
Mở vài ảnh trong thư mục `debug/` (đặc biệt file `..._2_otsu.png`) —
nếu chữ cái không rõ nét màu trắng trên nền đen, có thể do hiệu ứng
ánh sáng/VFX của boss làm nhiễu kênh đỏ. Báo lại ảnh đó để chỉnh
`CONFIDENCE_THRESHOLD` / `MARGIN_THRESHOLD` trong `main.py` cho phù hợp.
