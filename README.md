# 🔍 Hệ thống tìm kiếm người bằng mô tả CLIP  
*(Contrastive Language-Image Pre-Training)*

---

## 📁 Cấu trúc thư mục

```bash
ICFG-PEDES/
├── imgs/
│   ├── test/
│   └── ...
├── captions.csv
├── captions_cleaned.csv
├── ICFG-PEDES.json
├── invalid_paths.csv
preprocess.py
app.py
index.html
image_embeddings.npy
image_paths.npy
```
## ⚙️ Cài đặt

### 1. Clone repository:
```bash
git clone https://github.com/nvtan208/Xay-dung-he-thong-tim-kiem-nguoi
cd Xay-dung-he-thong-tim-kiem-nguoi
```
### 2. Tải dataset ICFG-PEDES (GitHub không lưu dữ liệu lớn):
Truy cập Kaggle ICFG-PEDES dataset

Tải file .zip về và giải nén vào thư mục dự án, đảm bảo cấu trúc thư mục giống như phần trên.

### 3. Tạo virtual environment (khuyến nghị):
```bash
python -m venv venv
source venv/bin/activate    # Linux/Mac
venv\Scripts\activate       # Windows
```
### 4. Cài đặt các package cần thiết:
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install transformers pillow pandas numpy tqdm flask flask-cors scikit-learn deep-translator
```
💡 Lưu ý: Chọn phiên bản torch tương thích với GPU nếu có.

## 🛠 Tiền xử lý dữ liệu ( KHÔNG CẦN CHẠY LẠI VÌ ĐÃ CÓ Ở CODE )
Trước khi chạy hệ thống, cần tạo embeddings từ ảnh:
```bash
python preprocess.py
```
Sẽ tạo ra:
<ul>
  <li>
      image_embeddings.npy: embeddings của tất cả ảnh
  </li>
  <li>
      image_paths.npy: đường dẫn ảnh tương ứng
  </li>
</ul>

## 🚀 Chạy ứng dụng
```bash
python app.py
```
<ul>
  <li>Server Flask sẽ chạy tại http://127.0.0.1:5000/</li>
  <li>Frontend truy cập tại: http://127.0.0.1:5000/</li>
</ul>

 ## 🖥 Giao diện frontend
<ul>
  <li>Nhập mô tả người (có thể bằng tiếng Việt) vào ô tìm kiếm.</li>
  <li>Hệ thống tự động dịch sang tiếng Anh và tìm ảnh tương ứng.</li>
  <li>Kết quả hiển thị dưới dạng lưới ảnh, click vào ảnh để xem lớn.</li>
</ul>

## 🔍 Công nghệ sử dụng

<ul>
  <li>Backend: Python, Flask, CLIP (Contrastive Language-Image Pre-Training)</li>
  <Li> Frontend: HTML, CSS, JavaScript</Li>
  <li>Dịch tiếng Việt → Anh: Deep-translator (Google Translate).</li>
  <li>Tìm kiếm ảnh: Cosine Similarity trên Embeddings.</li>
  <li>Dataset: ICFG-PEDES</li>
</ul>

## ⚡ Lưu ý
<ul>
  <li>Dataset không được lưu trên GitHub, cần tải riêng từ Kaggle.</li>
  <li>Nếu dataset quá lớn, việc tạo embeddings có thể mất thời gian.</li>
  <li>Chạy trên GPU sẽ nhanh hơn nhiều.</li>
  <li>Hệ thống hiện chưa triển khai caching hoặc batch inference tối ưu, thích hợp cho demo và thử nghiệm.</li>
</ul>
