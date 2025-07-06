# Nhận diện cảm xúc với mô hình ResEmoteNet

## 🎯 Mục đích đồ án
Tìm hiểu và thực nghiệm mô hình **ResEmoteNet** trong bài toán nhận diện cảm xúc.

## 📚 Mô tả chi tiết
Tất cả các thử nghiệm được thực hiện trên tập dữ liệu **RAF-DB**, bao gồm các kịch bản sau:

- Huấn luyện trên dữ liệu gốc (chưa tăng cường)
- Huấn luyện trên dữ liệu tăng cường bằng kỹ thuật tự triển khai

## 🖥️ Môi trường huấn luyện
Mô hình được huấn luyện trực tiếp trên nền tảng **Kaggle Notebooks**, sử dụng GPU do Kaggle cung cấp.  
Không cần thiết lập môi trường Conda thủ công.

## ⚙️ Hướng dẫn cài đặt (nếu chạy ngoài Kaggle)

Nếu muốn chạy mô hình trên máy cá nhân, có thể thực hiện các bước sau:

1. Tạo môi trường Conda:
```bash
conda create --name fer
conda activate fer
```

2. Cài đặt Python v3.8 sử dụng Conda
```bash
conda install python=3.8
```
3. Clone code
```bash
git clone https://github.com/ThanhDuy190304/Face-Emotion-Recognition---HCMUS.git
```
4. Cài đặt thư viện cần thiết
```bash
pip install -r requirement.txt
```
5. Tải dữ liệu
- Bước 1: Tải dataset
  - Tải dataset **RAF-DB** từ Kaggle.
- Bước 2: Tiền xử lý dữ liệu
  - Chuẩn hóa cấu trúc dữ liệu theo hướng dẫn của ResEmoteNet:  
    🔗 [data_preprocessing README.md](https://github.com/ArnabKumarRoy02/ResEmoteNet/blob/main/data_preprocessing/README.md)

  - Sau bước này, bạn cần đảm bảo dữ liệu được chia thành 3 tập: `train`, `val`, `test`.  
    Mỗi tập phải có 7 thư mục con ứng với 7 cảm xúc (đánh số từ `0` đến `6`).

  - Ngoài ra, cần có các file nhãn đi kèm:
    - `train_labels.csv`
    - `val_labels.csv`
    - `test_labels.csv`  
    Các file này nên có định dạng 2 cột: `image_name`, `class`.

- Bước 3: Tăng cường dữ liệu

  - Chạy notebook `augmentation.ipynb` để thực hiện tăng cường dữ liệu.
  - Các kỹ thuật bao gồm: xoay ảnh, lật ảnh, biến dạng Affine, biến dạng phối cảnh, tịnh tiến
  - Kết quả tăng cường sẽ được lưu trong một thư mục riêng (ví dụ: `augmented`) có cấu trúc tương tự như thư mục gốc.
  - Sau đó copy ảnh từ thư mục augmented vào thư mục gốc để làm giàu tập dữ liệu huấn luyện.
---

✅ **Lưu ý**:
- Việc tăng cường dữ liệu chỉ áp dụng cho tập `train`, không áp dụng cho `val` và `test`.


## 🚀 Sử dụng
1. Huấn luyện
```bash
python ResEmoteNet_train.py
```
2. Đánh giá
Tải các model từ [link Google Drive này](https://drive.google.com/drive/folders/1QHoIC8TJ9ZThx-h6ls60G2wZ_Liu9uuG?usp=drive_link) và đặt vào thư mục `model` trong thư mục gốc dự án.



