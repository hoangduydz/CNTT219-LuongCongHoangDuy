# A2 02 Phân tích dữ liệu hành khách Titanic

Lương Công Hoàng Duy (240464), 60%. Lê Nguyễn Gia Bảo (240233), 40%.

Python và Pandas EDA. Tầng Cơ bản theo đề A2-02. Không huấn luyện mô hình học máy.

## Ba câu hỏi của đề

1. Những yếu tố nào liên quan tới khả năng sống sót?
2. Giả thuyết “phụ nữ và trẻ em trước” có được phản ánh trong dữ liệu không?
3. Hạng vé có ảnh hưởng độc lập với giới tính không, hay chỉ là biến trung gian?

## Dữ liệu

Dùng `train.csv` của Kaggle Titanic: 891 hành khách, 12 cột, có nhãn Survived.
Không trộn với bản OpenML 1.309 dòng hoặc Kaggle test.csv không có nhãn.

Nguồn: https://www.kaggle.com/competitions/titanic/data

Đọc và tuân thủ quy tắc: https://www.kaggle.com/competitions/titanic/rules

Repo dùng link nguồn thay vì phát hành lại CSV. Đăng nhập Kaggle, tải dữ liệu,
giải nén và đặt `train.csv` ngay trong thư mục A2.

SHA256 bản CSV dùng phân tích: `4a437fde05fe5264e1701a7387ac6fb75393772ba38bb2c9c566405af5af4bd7`.
Nếu bản tải khác mã băm do kiểu xuống dòng, đối chiếu nội dung và cấu trúc trước khi thay assert; không bỏ kiểm tra để che khác biệt dữ liệu.

## Cách chạy lại

Yêu cầu Python 3.10 trở lên. Mở terminal tại thư mục A2:

```bash
python -m venv .venv
```

Windows PowerShell: `.venv\Scripts\Activate.ps1`.
macOS/Linux: `source .venv/bin/activate`.

```bash
python -m pip install -r requirements.txt
python -m notebook
```

Mở `A2-02_Titanic_Kaggle891.ipynb`, chọn Restart Kernel rồi Run All từ đầu đến cuối.
Trên Colab: mở notebook, tải train.csv lên Files, chọn Runtime > Run all.
Không cần API key và không tải dữ liệu tự động từ nguồn khác.

## Các tệp chính

- `A2-02_Titanic_Kaggle891.ipynb`: notebook còn nguyên kết quả và 9 biểu đồ.
- `A2-02_BaoCao_8Trang_240464_240233.pdf`: báo cáo chính đúng 8 trang, 6 biểu đồ.
- `A2-02_Slide_Kaggle891_240464_240233.pptx`: 12 slide, gồm 9 trang chính và 3 phụ lục.
- `HUONG_DAN_THUYET_TRINH.md`: lời trình bày và câu hỏi/đáp để ôn.
- `requirements.txt`: thư viện cần cài.

[Mở notebook trên Colab](https://colab.research.google.com/github/hoangduydz/CNTT219-LuongCongHoangDuy/blob/main/A2/A2-02_Titanic_Kaggle891.ipynb).
Sau khi mở, tải `train.csv` vào Files rồi Run all. Đây là bản Kaggle mới,
khác notebook OpenML cũ đang nằm trong Google Drive.

## Kết quả kiểm chứng

Notebook đã chạy 11 ô mã trong kernel mới, 0 lỗi, 14 nhóm assert đạt và 9 biểu đồ.
Kết quả kiểm tra: 891 hồ sơ, 342 người sống; tuổi quan sát 714 hồ sơ, 290 người sống.
CSV thiếu Age 177, Cabin 687, Embarked 2; không có dòng trùng hoàn toàn.

Môi trường kiểm chứng: Python 3.12.14, Pandas 3.0.6, NumPy 2.5.4,
Matplotlib 3.10.8, Seaborn 0.13.2. Notebook còn nguyên kết quả và hình.
Các biểu đồ PNG được tạo vào `figures/` khi chạy lại.

Commit thứ nhất ghi phạm vi và nguồn; lần bổ sung này đưa notebook đã chạy và môi trường.
Lần hoàn thiện thêm PDF 8 trang và slide đã cập nhật toàn bộ số liệu Kaggle.
Các commit là lần chỉnh sửa thực,
không lùi ngày và không đại diện cho lịch sử làm nhiều tuần.

## Khai báo AI

OpenAI Codex hỗ trợ tổ chức mã, soạn diễn giải và kiểm tra kỹ thuật.
Hai thành viên cần tự chạy lại, đối chiếu mẫu số và giải thích mọi dòng mã.

## Phạm vi diễn giải

Kết luận mô tả mẫu lịch sử. Phân tầng giới tính × hạng vé không chứng minh
tác động nhân quả độc lập hoặc vai trò trung gian. Không dùng tỷ lệ nhóm để
đánh giá cá nhân hiện tại.
