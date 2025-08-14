# Bayesian Cluster Validity Index (BCVI)

## 1. Giới thiệu tổng quan
Phân cụm (Clustering) là một công cụ học không giám sát quan trọng trong thống kê và học máy, được sử dụng để nhóm các quan sát thành các nhóm có hành vi tương đồng. Một bước thiết yếu trong quá trình phân cụm là đánh giá tính hợp lý của số lượng cụm, thường được thực hiện thông qua các **Chỉ số Xác thực Cụm (Cluster Validity Index - CVI)**.

Dự án này tập trung nghiên cứu và phát triển một chỉ số mới có tên **Bayesian Cluster Validity Index (BCVI)**. BCVI được xây dựng dựa trên các CVI hiện có và sử dụng phân phối tiên nghiệm Dirichlet và Dirichlet tổng quát. BCVI cho phép tích hợp kiến thức chuyên môn của người dùng để lựa chọn số lượng cụm tối ưu, mang lại sự linh hoạt tùy chỉnh theo nhu cầu ứng dụng. Nó có thể áp dụng cho cả thuật toán phân cụm cứng (như K-Means) và phân cụm mềm (như Fuzzy C-Means).

## 2. Mục tiêu nghiên cứu
Mục tiêu chính của báo cáo này là phát triển chỉ số BCVI để đánh giá tính hợp lý của số lượng cụm trong bài toán phân cụm dữ liệu, đặc biệt là phân cụm hình ảnh và dữ liệu thực tế. BCVI giúp xác định số cụm tối ưu, cải thiện khả năng xác định số lượng cụm tối ưu và cho kết quả chính xác hơn so với các chỉ số CVI truyền thống.

## 3. Phương pháp và thuật toán sử dụng

### 3.1. Thuật toán phân cụm
- **K-Means**: Một thuật toán phân cụm đơn giản nhưng hiệu quả, chia dữ liệu thành k cụm bằng cách gán mỗi điểm dữ liệu vào trọng tâm gần nhất và cập nhật trọng tâm cho đến khi hội tụ. Mục tiêu là giảm thiểu tổng bình phương trong cụm (WCSS).
- **Fuzzy C-Means (FCM)**: Một kỹ thuật phân cụm mềm, gán cho mỗi điểm dữ liệu một mức độ thành viên, biểu thị mức độ thuộc về từng cụm. Mục tiêu là giảm thiểu hàm mục tiêu dựa trên mức độ thành viên và khoảng cách đến trọng tâm cụm.

### 3.2. Các chỉ số đánh giá cụm truyền thống (CVI)
Các chỉ số này được sử dụng làm cơ sở cho việc đánh giá BCVI:

**Phân cụm cứng:**
- Calinski-Harabasz (CH)
- Chỉ số xác thực cụm dựa trên các điểm gần nhất (CVNN)
- Davies-Bouldin (DB)
- Silhouette (SH)
- Starczewski (STR)
- Wiroonsri (WI)

**Phân cụm mềm:**
- KWON2
- Wiroonsri và Preedasawakul (WP)
- Xie và Beni (XB)

### 3.3. Thuật toán Bayesian Cluster Validity Index (BCVI)
BCVI kết hợp kiến thức tiên nghiệm với dữ liệu thực tế, sử dụng phân phối Dirichlet và Dirichlet tổng quát để xác định số cụm tối ưu.

Các bước chính:
1. **Xác định các chỉ số hiệu lực cụm ban đầu**: Chọn một hoặc nhiều CVI truyền thống làm cơ sở.
2. **Áp dụng phân phối Dirichlet hoặc Dirichlet tổng quát**: Sử dụng các phân phối này để thiết lập xác suất tiên nghiệm (prior) cho số lượng cụm dựa trên kinh nghiệm hoặc kiến thức chuyên môn của người dùng.
3. **Tính toán phân phối hậu nghiệm (posterior)**: Dựa trên dữ liệu và phân phối tiên nghiệm, tính toán phân phối hậu nghiệm để đưa ra xác suất cho các số lượng cụm có thể xảy ra.
4. **Lựa chọn số lượng cụm tối ưu**: Số cụm tối ưu hoặc các cực đại cục bộ được chọn dựa trên các xác suất hậu nghiệm, cho phép người dùng linh hoạt trong việc chọn số cụm phù hợp nhất.

**Tính chất của BCVI:**
- **Linh hoạt**: Cho phép điều chỉnh theo kiến thức tiên nghiệm.
- **Nghiệm hậu**: Kết hợp dữ liệu với kiến thức trước.
- **Khả năng cung cấp lựa chọn phụ**: Phát hiện các đỉnh cục bộ trong phân phối hậu nghiệm.
- **Độ chính xác**: Cải thiện việc xác định số lượng cụm.

## 4. Ứng dụng thực nghiệm

### 4.1. Dữ liệu sử dụng
- **Dữ liệu nhân tạo**: Được tạo từ phân phối Gaussian và Uniform (lấy từ GitHub của O-PREEDASAWAKUL 2023). Dữ liệu này giúp kiểm soát yếu tố nhiễu và đánh giá hiệu suất của BCVI trong điều kiện lý tưởng.
- **Dữ liệu thực tế**: Dry Bean Dataset từ UCI Machine Learning Repository (M. Koklu, Ilker Ali Özkan, 2020). Bộ dữ liệu này gồm 7 loại đậu có đặc điểm tương đồng, được dùng để kiểm tra khả năng của BCVI trong môi trường thực tế.
- **Ảnh MRI não**: Dữ liệu gốc từ bài báo BCVI đã nghiên cứu trước đó, sử dụng cho bài toán phát hiện khối u não.

### 4.2. Các bước thực nghiệm
1. Tiền xử lý ảnh: Chuẩn hóa kích thước ảnh về 128x128 pixels và chuẩn hóa pixel.
2. Áp dụng K-Means và FCM để phân cụm.
3. Đánh giá các chỉ số phân cụm với và không có BCVI.
4. Thử nghiệm nhiều giá trị K và các chỉ số CVI.

## 5. Kết quả nổi bật
- BCVI giúp cải thiện khả năng xác định số lượng cụm tối ưu.
- Trong phát hiện khối u não, BCVI xác định số cụm tối ưu **K = 4**. Với K=5, K-means cũng phân đoạn được khối u não.
- Độ chính xác phân cụm dữ liệu thực tế đạt trên 75%.
- BCVI cho phép điều chỉnh kết quả phân cụm sai do CVI cơ bản đưa ra.

## 6. Ứng dụng tiềm năng
- **Y tế**: Xử lý ảnh MRI, phát hiện khối u.
- **Marketing**: Phân khúc khách hàng.
- **Nghiên cứu khoa học**: Sinh học, xã hội học.
- **Big Data**: Xử lý dữ liệu lớn.

## 7. Hạn chế của nghiên cứu
- Phụ thuộc vào việc chọn giá trị α.
- Độ nhạy với kích thước dữ liệu.
- Ảnh hưởng từ chất lượng dữ liệu.
- Giới hạn với các CVI cơ bản.
- Không phù hợp cho mọi loại dữ liệu.
- Dữ liệu nhân tạo không phản ánh hoàn toàn thực tế.

## 8. Hướng phát triển tiếp theo
1. Thử nghiệm BCVI trên tập dữ liệu y tế lớn hơn.
2. Tích hợp BCVI vào hệ thống hỗ trợ chẩn đoán.
3. Mở rộng BCVI cho các loại phân phối tiên nghiệm khác.
4. Kiểm tra hiệu suất trên dữ liệu phức tạp hơn.