# A2 02 Phân tích dữ liệu hành khách Titanic

Lương Công Hoàng Duy (240464), 60%. Lê Nguyễn Gia Bảo (240233), 40%.

Phân tích khám phá bằng Python, Pandas, Matplotlib và Seaborn. Tầng Cơ bản theo đề A2-02.

Repo: https://github.com/hoangduydz/CNTT219-LuongCongHoangDuy/tree/main/A2

## Ba câu hỏi của đề

1. Những yếu tố nào liên quan tới khả năng sống sót?
2. Giả thuyết “phụ nữ và trẻ em trước” có được phản ánh trong dữ liệu không?
3. Hạng vé có ảnh hưởng độc lập với giới tính không, hay chỉ là biến trung gian?

## Sản phẩm

Các tệp trên GitHub giữ tên cũ để các liên kết đã chia sẻ vẫn hoạt động. Bản ZIP nộp dùng tên thống nhất theo MSSV hai thành viên.

| Sản phẩm | Tên trong ZIP | Tên trong thư mục A2 trên GitHub |
| --- | --- | --- |
| Notebook đã chạy | `A2_240464_240233_PhanTich.ipynb` | `A2-02_Titanic_Kaggle891.ipynb` |
| Báo cáo PDF 8 trang | `A2_240464_240233_BaoCao.pdf` | `A2-02_BaoCao_8Trang_240464_240233.pdf` |
| Báo cáo Word | `A2_240464_240233_BaoCao.docx` | `A2-02_BaoCao_240464_240233.docx` |
| PowerPoint nền sáng | `A2_240464_240233_ThuyetTrinh.pptx` | `A2-02_Slide_Kaggle891_240464_240233.pptx` |

Notebook giữ nguyên kết quả, 11 ô mã và 9 biểu đồ. Báo cáo PDF có 8 trang tính cả bìa, 5 biểu đồ kèm diễn giải. Bản Word có logo trường, phông Times New Roman và bìa ghi tên, MSSV hai thành viên.

PowerPoint gồm 7 slide chính và 3 phụ lục, nền trắng/ngà với điểm nhấn nâu đồng. Phần Notes chứa lời dẫn và số liệu để tập bài nói khoảng 5 phút. Hướng dẫn hỏi đáp trên repo ở `HUONG_DAN_THUYET_TRINH.md`; đây là tài liệu ôn tập bổ sung.

ZIP còn có `train.csv`, `figures/`, `requirements.txt` và `LINK_GITHUB.txt`. Các biểu đồ trong `figures/` có thể tạo lại bằng notebook.

## Dữ liệu và nguồn

Dùng `train.csv` của Kaggle Titanic: 891 hành khách, 12 cột, có nhãn Survived.

Nguồn dữ liệu: https://www.kaggle.com/competitions/titanic/data

Quy tắc sử dụng: https://www.kaggle.com/competitions/titanic/rules

Repo công khai cung cấp link nguồn thay cho CSV gốc. Khi chạy từ GitHub, đăng nhập Kaggle, tải dữ liệu, giải nén và đặt `train.csv` ngay cạnh notebook trong thư mục A2. Bản ZIP nộp có CSV dùng cho phân tích.

SHA256 của CSV: `4a437fde05fe5264e1701a7387ac6fb75393772ba38bb2c9c566405af5af4bd7`.
Nếu bản tải khác mã băm do kiểu xuống dòng, đối chiếu nội dung và cấu trúc trước khi sửa điều kiện kiểm tra.

Ảnh bìa slide: *RMS Titanic 3*, F. G. O. Stuart, 10/04/1912. Wikimedia Commons ghi phạm vi công cộng. Nguồn và tình trạng bản quyền: https://commons.wikimedia.org/wiki/File:RMS_Titanic_3.jpg .

## Chạy lại trên máy

Khuyến nghị Python 3.12. Mở terminal trong thư mục có notebook và `requirements.txt`:

```bash
python -m venv .venv
```

Windows PowerShell: `.venv\Scripts\Activate.ps1`.
macOS/Linux: `source .venv/bin/activate`.

```bash
python -m pip install -r requirements.txt
python -m notebook
```

Mở notebook theo tên tương ứng ở bảng trên. Kiểm tra `train.csv` nằm cùng thư mục, chọn Restart Kernel rồi Run All từ đầu đến cuối. Notebook ghi các biểu đồ vào `figures/`.

## Chạy trên Google Colab

[Mở notebook trên Colab](https://colab.research.google.com/github/hoangduydz/CNTT219-LuongCongHoangDuy/blob/main/A2/A2-02_Titanic_Kaggle891.ipynb).

Tải `train.csv` vào Files, chọn Runtime > Run all. Không cần API key.

## Kiểm chứng

Bản notebook đã chạy 11 ô mã trong kernel mới, không có lỗi, 14 nhóm assert đạt và có 9 biểu đồ. Kết quả: 891 hồ sơ, 342 người sống; 714 hồ sơ có tuổi quan sát, trong đó 290 người sống. Age thiếu 177, Cabin thiếu 687, Embarked thiếu 2; không có dòng trùng hoàn toàn.

Môi trường tạo kết quả trong notebook: Python 3.12.14, Pandas 3.0.6, NumPy 2.5.4, Matplotlib 3.10.8, Seaborn 0.13.2. `requirements.txt` khai báo khoảng phiên bản để cài môi trường tương thích.

Chênh lệch tính từ tỷ lệ chưa làm tròn: nữ và nam 55,3 điểm phần trăm; trẻ em nam và nam >12 tuổi 39,4 điểm phần trăm; nữ hạng 1 và nữ hạng 3 là 46,8 điểm phần trăm.

Các commit ghi các lần chỉnh sửa thực, giữ nguyên lịch sử đã có.

## Khai báo AI và phạm vi diễn giải

OpenAI Codex hỗ trợ tổ chức mã, soạn diễn giải, thiết kế tài liệu và kiểm tra kỹ thuật. Hai thành viên cần tự chạy lại, đối chiếu mẫu số và giải thích được mọi dòng mã.

A2 tập trung EDA, không huấn luyện mô hình học máy. Kết luận mô tả mẫu lịch sử. Phân tầng giới tính × hạng vé chưa chứng minh tác động nhân quả độc lập hoặc cơ chế trung gian. Tỷ lệ nhóm không xác định kết quả của từng cá nhân.
