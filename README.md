This version is written in Vietnamese, if you don't understand, use Google Translate

The code section is in the "master" branch.
![image](https://github.com/user-attachments/assets/e386dfbe-c4ed-47c3-be24-c1d734281941)

# Inventory-Management-System-Spring-Boot (Quản lí kho hàng Spring Boot)

Các tổ chức, công ti cần sử dụng hệ thống quản lý để phân bố hóa nhiệm vụ của họ. Chúng có thể đơn giản hoặc phức tạp tùy thuộc vào nhu cầu của tổ chức. Hệ thống quản lý hàng tồn kho (hoặc hệ thống hàng tồn kho) là quy trình mà bạn theo dõi hàng hóa của mình trong toàn bộ chuỗi cung ứng, từ mua hàng đến sản xuất đến bán hàng cuối cùng. Nó chi phối cách bạn tiếp cận quản lý hàng tồn kho cho doanh nghiệp của mình.

Hệ thống quản lý hàng tồn kho dựa trên web sẽ cố gắng tự động hóa và thay thế cách tiếp cận dựa trên giấy truyền thống để quản lý và theo dõi hàng tồn kho đang được sử dụng. Thay cho công việc dựa trên giấy tờ mất rất nhiều thời gian, hệ thống sẽ được tạo cho các hoạt động về cung cầu hàng hóa, giao dịch và sẽ đóng vai trò như một cơ sở dữ liệu trung tâm, nơi việc tìm kiếm một bản ghi duy nhất trong thời gian ngắn. Hệ thống quản lý không cần giấy tờ này sẽ tăng hiệu quả, giảm độ phức tạp và mang lại sự linh hoạt cho tổ chức.

Dự án này bao gồm đăng nhập, đăng ký, đăng xuất, CRUD các hệ thống được nêu ở dưới
# Entity Relationship Diagram
![image](https://github.com/user-attachments/assets/59718a5f-7ce2-48d1-a9af-732e1f4c36d0)

Dựa vào ERD của dự án, các chức năng chính mà hệ thống quản lý kho hàng bao gồm:

1. Quản lý thông tin sản phẩm

Chức năng:

Thêm mới, sửa đổi, xóa thông tin sản phẩm.

Tra cứu thông tin chi tiết sản phẩm: tên, loại, trạng thái, số lượng, giá, nhà cung cấp.

Liên quan đến bảng:

- inventory_item: Lưu trữ thông tin chi tiết về sản phẩm.

- item_type: Xác định loại sản phẩm, giúp phân loại dễ dàng.

- vendor: Quản lý nhà cung cấp sản phẩm.

2. Quản lý loại sản phẩm

Chức năng:

Thêm mới, cập nhật, xóa loại sản phẩm.

Liệt kê danh mục các loại sản phẩm hiện có.

Liên quan đến bảng:

- item_type: Lưu trữ thông tin về loại sản phẩm.

3. Quản lý nhập kho và sửa chữa sản phẩm

Chức năng:

Theo dõi các sản phẩm được nhập từ nhà cung cấp.

Quản lý thông tin các sản phẩm cần sửa chữa, chi phí và ngày sửa chữa.

Liên quan đến bảng:

- vendor: Quản lý nhà cung cấp của sản phẩm nhập kho.

- item_repair: Lưu thông tin các sản phẩm đã sửa chữa.

4. Quản lý mượn và trả sản phẩm

Chức năng:

Theo dõi các sản phẩm đang được mượn bởi khách hàng.

Ghi nhận thông tin mượn trả: ngày mượn, ngày trả, thời gian mượn, phí phạt nếu trả trễ.

Kiểm tra lịch sử mượn trả của khách hàng.

Liên quan đến bảng:

- loan: Lưu trữ thông tin mượn trả sản phẩm.

- borrower: Quản lý thông tin người mượn.

5. Quản lý thông tin người dùng

Chức năng:

Quản lý thông tin người mượn hàng (khách hàng): email, tên, ID.

Quản lý thông tin nhân viên (quản lý kho): email, loại nhân viên.

Liên quan đến bảng:

- borrower: Lưu thông tin khách hàng mượn sản phẩm.

- inventory_manager: Lưu thông tin nhân viên quản lý kho.

- manager_type: Xác định loại nhân viên (quản trị viên, nhân viên thường).

6. Quản lý nhà cung cấp

Chức năng:

Thêm mới, cập nhật, xóa thông tin nhà cung cấp.

Liệt kê danh sách các nhà cung cấp và thông tin chi tiết của từng nhà cung cấp.

Liên quan đến bảng:

- vendor: Lưu thông tin nhà cung cấp.

7. Báo cáo và phân tích

Chức năng:

Tạo báo cáo số lượng hàng tồn kho theo loại sản phẩm, nhà cung cấp.

Theo dõi sản phẩm đang mượn, đã mượn, sản phẩm cần sửa chữa.

Phân tích dữ liệu về chi phí sửa chữa, doanh thu từ phí mượn trả.

Liên quan đến bảng:

- inventory_item, loan, item_repair, vendor.

8. Quản lý tài chính

Chức năng:

Quản lý phí mượn trả của khách hàng.

Theo dõi chi phí sửa chữa sản phẩm.

Báo cáo tổng chi phí và doanh thu hàng tháng.

Liên quan đến bảng:

- loan: Lưu thông tin phí phạt khi trả trễ.

- item_repair: Lưu thông tin chi phí sửa chữa.

9. Tìm kiếm và tra cứu

Chức năng:

Tìm kiếm nhanh thông tin sản phẩm, khách hàng, nhân viên, nhà cung cấp.

Lọc và phân loại sản phẩm theo tình trạng, loại, số lượng tồn kho.

Liên quan đến bảng:

Toàn bộ các bảng: hỗ trợ tìm kiếm thông tin cần thiết.

10. Phân quyền người dùng

Chức năng:

Phân quyền truy cập hệ thống theo vai trò (admin, nhân viên, khách hàng).

Đảm bảo chỉ admin có quyền chỉnh sửa, xóa dữ liệu quan trọng.

Liên quan đến bảng:

- inventory_manager, manager_type: Quản lý quyền hạn của nhân viên.
# Tech Stack
- Spring Boot
- Thymeleaf
- MySQL
- Hibernate
# Project Status: In-Progress
Thiếu mục quản lí nhân viên và phân quyền
