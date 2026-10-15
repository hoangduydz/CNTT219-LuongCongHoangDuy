# Học nhanh và hỏi đáp A2 Titanic Kaggle 891

Lương Công Hoàng Duy 240464 và Lê Nguyễn Gia Bảo 240233.
Chỉ dùng số liệu bản 891 dòng. Không đọc các tỷ lệ của bản OpenML cũ.

## Trình bày trong khoảng 5 phút

Slide 1, khoảng 15 giây: giới thiệu bài toán, hai thành viên và mục tiêu phân tích.

Slide 2, khoảng 25 giây: nêu ba câu hỏi chính thức. 74,2% là tỷ lệ sống của nữ;
58,0% là tỷ lệ sống của trẻ ≤12 trong mẫu có tuổi; 46,8 điểm phần trăm là chênh
giữa nữ hạng 1 và nữ hạng 3. Các con số là bằng chứng mở đầu, cần giải thích ở các slide sau.

Slide 3, khoảng 45 giây: “Chúng em dùng train.csv Kaggle có 891 hồ sơ, 12 cột.
Age thiếu 177 và Cabin thiếu 687. Giữ CSV gốc, bỏ Cabin khỏi bảng phân tích,
không tự xóa giá vé cao. Bảng chính vẫn giữ 891 người, riêng tuổi dùng 714 tuổi quan sát.”

Slide 4, khoảng 40 giây: “Nữ có tỷ lệ sống 74,2%, nam là 18,9%, chênh 55,3 điểm
phần trăm. Đây là liên hệ mô tả, chưa xếp hạng tác động độc lập của các yếu tố.”

Slide 5, khoảng 55 giây: “Giả thuyết phụ nữ và trẻ em trước có hỗ trợ mô tả một phần.
Trẻ em gộp 58,0%, nhóm >12 là 38,8%. Trong nam, trẻ em 56,8% cao hơn 17,3%;
trong nữ, trẻ em 59,4% thấp hơn 77,7%. Vì vậy không cùng chiều ở mọi nhóm.
Tỷ lệ sống cũng không cho biết trình tự ưu tiên sơ tán.”

Slide 6, khoảng 60 giây: “Khi giữ cùng giới tính, hạng 1 vẫn cao hơn hạng 3.
Trong nữ là 96,8% so với 50,0%, trong nam là 36,9% so với 13,5%.
Liên hệ hạng vé không chỉ do cơ cấu giới ở mẫu gộp. Chưa thể kết luận nhân quả
độc lập hoặc cơ chế trung gian vì chưa loại hết các yếu tố khác.”

Slide 7, khoảng 45 giây: chốt ba nhận định kèm giới hạn. Ba chênh lệch là 55,3 điểm
phần trăm (nữ so với nam), 39,4 điểm phần trăm (trẻ em nam so với nam >12),
46,8 điểm phần trăm (nữ hạng 1 so với nữ hạng 3). Tính từ tỷ lệ gốc rồi mới làm tròn:
(21/37 − 72/416) × 100 = 39,449..., làm tròn một chữ số là 39,4.

Tổng lời nói khoảng 4 phút 45 giây, dành phần còn lại để chuyển slide.
Phân công 60/40 và khai báo AI nằm ở bìa. Phần Notes của PowerPoint có lời dẫn đầy đủ.
Không đọc toàn bộ bảng. Chỉ rõ tử số, mẫu số và điều kết quả chưa chứng minh.
Ba slide 8–10 chỉ mở khi hỏi đáp. Mỗi thành viên cần chuẩn bị trình bày toàn bài,
không mặc định tỷ lệ công việc 60/40 là tỷ lệ thời gian nói.

## Câu hỏi và câu trả lời

### 1. Bài này có phải học máy không?

Không. A2 đánh giá Pandas, làm sạch, EDA và trực quan hóa. Không huấn luyện mô hình,
không chia train/test để dự đoán. Tên train.csv chỉ là tên tệp có nhãn từ cuộc thi.

### 2. Vì sao chỉ dùng 891 dòng?

Đây là tệp train.csv có Survived của Kaggle, đúng dữ liệu đề A2-02 nêu.
Không ghép test.csv không có nhãn. Không thêm dòng hoặc ngày giả.
Đề xếp Titanic tầng Cơ bản, điểm trần 8,0; làm thêm mô hình không tự nâng tầng.

### 3. mean của Survived tại sao là tỷ lệ sống?

Survived chỉ có 0 và 1. Tổng bằng số người sống, trung bình bằng tổng số sống chia
số kết quả có mặt. Nữ: 233 / 314 = 74,2%. Không so sánh bằng số người sống tuyệt đối
vì nữ và nam có quy mô khác nhau.

### 4. 55,3 điểm phần trăm khác 55,3% thế nào?

74,2038% − 18,8908% = 55,3130 điểm phần trăm. Đây là hiệu hai tỷ lệ.
Không gọi hiệu này là phần trăm tăng tương đối.

### 5. Vì sao không dropna toàn bộ dữ liệu?

Cabin thiếu 77,1%. Xóa mọi dòng có bất kỳ ô thiếu sẽ làm mất nhiều hành khách
không cần thiết. Chọn theo biến của câu hỏi: giới và hạng vé dùng 891, tuổi dùng 714.

### 6. Vì sao chọn không điền tuổi ở phân tích chính?

Để tránh xem tuổi ước lượng là tuổi thật. Nhược điểm là còn 714 hồ sơ và có thể
bị thiên lệch chọn mẫu. Vì vậy bổ sung hai chiến lược điền trung vị để so sánh.

### 7. Ba chiến lược Age là gì?

A: giữ tuổi quan sát, n=714. B: điền trung vị chung 28, n=891.
C: điền trung vị sex × pclass, n=891. B/C điền 177 ô, không dùng Survived làm biến điền.
Độ lệch chuẩn lần lượt 14,53; 13,02; 13,30. Giảm độ phân tán không chứng minh chính xác hơn.

### 8. Vì sao số trẻ em không đổi khi điền tuổi?

Các trung vị được dùng đều >12 nên tuổi điền được xếp vào nhóm >12.
Số trẻ giữ 69, nhóm >12 tăng từ 645 lên 822. Đây là hệ quả phương pháp điền,
không phải bằng chứng tất cả 177 người thiếu tuổi thực sự >12.

### 9. Cabin bị bỏ có nghĩa là không có giá trị không?

Không. Cabin thiếu 687/891 và không cần trực tiếp cho ba câu hỏi nên bỏ khỏi bảng
phân tích; CSV gốc vẫn giữ. Nghiên cứu vị trí trên tàu có thể cần Cabin và cách xử lý khác.

### 10. Vì sao giữ giá vé cao và giá vé bằng 0?

IQR gắn cờ 116 dòng >65,6344, nhưng mức giá cao chưa đủ coi là sai.
Có 15 giá vé bằng 0, khác với thiếu; Fare không có ô thiếu. Không tự xóa hoặc đổi thành NaN.

### 11. Đã chứng minh “phụ nữ và trẻ em trước” chưa?

Chưa chứng minh trình tự cứu hộ. Tỷ lệ nữ và trẻ em gộp cao hơn tạo hỗ trợ mô tả,
nhưng tuổi không cùng chiều ở mọi giới. Không có biến thứ tự sơ tán để khẳng định
ai được ưu tiên trước trong thực tế.

### 12. Vì sao trẻ em nữ thấp hơn nữ >12 mà kết luận trẻ em gộp cao hơn?

Các phép gộp có thành phần và mẫu số khác nhau. Trẻ em gồm nữ và nam; lợi thế tuổi
rõ trong nam nhưng không cùng chiều trong nữ. Vì vậy phải xét bảng tuổi × giới,
không dùng một tỷ lệ gộp để khẳng định cho mọi nhóm.

### 13. Có thể gọi nhóm >12 là người lớn không?

Không gọi toàn bộ là người trưởng thành, vì còn gồm thiếu niên. Bài công bố đúng
ngưỡng phân tích ≤12 so với >12, không biến nó thành một quy chuẩn tuổi chung.

### 14. Bảng chéo câu 3 đọc thế nào?

Giữ cùng hàng nữ hoặc nam, so sánh các cột hạng vé. Nữ hạng 1/2/3: 91/94,
70/76, 72/144. Nam: 45/122, 17/108, 47/347. Tổng sáu ô là 891 người, 342 sống.
Hạng 1 cao hơn hạng 3 trong cả hai giới.

### 15. Vậy hạng vé có ảnh hưởng độc lập hay là trung gian?

Cách nói đúng với phạm vi bài: liên hệ hạng vé còn sau phân tầng giới tính,
không chỉ do cơ cấu giới ở mẫu gộp. Chưa chứng minh tác động nhân quả độc lập
hoặc vai trò trung gian. Phân tích trung gian cần cơ chế và thứ tự nhân quả,
không thể xác định chỉ từ bảng chéo.

### 16. Tại sao quy mô 4 cao nhất, không phải 1 hoặc 5?

Quan sát là 21/29=72,4% ở nhóm 4, 163/537=30,4% ở nhóm 1 và 3/15=20,0% ở nhóm 5.
Nhóm 4 có 65,5% nữ so với nhóm 1 chỉ 23,5%; nhóm 5 có 80,0% hạng 3 so với
nhóm 4 là 31,0%. Thành phần khác nhau là gợi ý, chưa giải thích toàn bộ chênh lệch.
Không nói hỗ trợ gia đình hoặc phối hợp cứu hộ là nguyên nhân đã được đo.

### 17. n=29 của quy mô 4 có phải 29 gia đình không?

Không. Đó là 29 hành khách có family_size=4. Các dòng có thể thuộc cùng gia đình,
nên không coi họ là 29 gia đình độc lập. Family_size = SibSp + Parch + 1 có cả bản thân.

### 18. Tại sao không vẽ quy mô 8 và 11?

Quy mô 8 có 6 người, quy mô 11 có 7 người; biểu đồ chỉ vẽ nhóm n≥10 để bớt
diễn giải tỷ lệ từ nhóm rất nhỏ. Dữ liệu và bảng tổng hợp vẫn giữ các nhóm này.

### 19. Các hàm Pandas quan trọng có tác dụng gì?

read_csv đọc CSV; isna().sum đếm thiếu; to_numeric kiểm soát kiểu số; groupby
chia nhóm; agg tính n/sum/mean; crosstab tạo bảng chéo; transform trả kết quả
nhóm về từng dòng; cut phân tuổi theo ngưỡng; dropna(subset=['age']) chỉ bỏ
tuổi thiếu khỏi phép phân tích tuổi.

### 20. Kiểm chứng được gì và chưa kiểm chứng được gì?

Kernel mới chạy 11 ô mã không lỗi. 14 nhóm assert kiểm tra shape, mã hồ sơ duy nhất,
miền giá trị, tuổi thiếu, tổng số sống và SHA256. Các kiểm tra xác nhận tính nhất quán
của xử lý trên CSV này, không chứng minh mọi hồ sơ lịch sử chính xác hoặc quan hệ nhân quả.

### 21. Repo có dữ liệu không?

Repo dùng link Kaggle thay CSV gốc; README chỉ cách tải và đặt train.csv.
Bản ZIP dùng để kiểm tra cục bộ có CSV đã dùng. Không tự gán một giấy phép mở
cho dữ liệu cuộc thi hoặc khẳng định được phép phát hành lại trên mọi nền tảng.

### 22. AI đã làm phần nào?

Codex hỗ trợ tổ chức mã, bản thảo, đối chiếu số liệu và kiểm tra kỹ thuật.
Hai thành viên phải tự chạy và hiểu bài. Không nói đã tự làm một bước nếu chưa thực hiện.
