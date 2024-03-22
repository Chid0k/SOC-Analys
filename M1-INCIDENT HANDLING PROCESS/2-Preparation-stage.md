# Preparation Stage Part 1
---
Trong giai đoạn chuẩn bị đầu tiên chúng tôi xác định 2 mục tiêu riêng biệt. **Đầu tiên**: Thiết lập chức năng xử lý sự cố trong tổ chức. **Thứ hai:** Thực hiện các chức năng bảo vệ thích hợp.

## [+] Điều kiện tiên quyết - Preparation Prerequisites
Chúng ta cần đảm bảo các yêu cầu sau:
- Kỹ năng xử lý sự cố của các thành viên. 
- Nhân lực được đào tạo 
- Chính sách và tài liệu rõ ràng
- Các công cụ: phần cứng và phần mềm.
## [+] Chính sách và tài liệu rõ ràng.
Các thông tin cần có trong chính sách và tài liệu:
- Thông tin liên hệ và vai trò các thành viên trong nhóm IH
- Thông tin liên hệ của bộ phận pháp lý và tuân thủ, nhóm quản lý, bộ phận hỗ trợ CNTT, bộ phận truyền thông và quan hệ truyền thông, cơ quan thực thi pháp luật, nhà cung cấp dịch vụ internet, quản lý cơ sở và nhóm ứng phó sự cố bên ngoài
- Chính sách, kế hoạch, thủ tục ứng phó sự cố (_Incident response_).
- Chính sách và thủ tục chia sẻ thông tin sự cố (_Incident information_).
- Đường cơ sở (_baseline_) của hệ thống và mạng. 
- Sơ đồ mạng (_Network diagrams_)
- Cơ sở dữ liệu quản lí tài sản trên toàn bộ tổ chức (_Organization-wide asset management database_)
- Tài khoản người dùng với đặc quyền cao.
- Khả năng có được phần cứng, phần mềm hoặc tài nguyên.
- Cheat sheets Forensic/Investigative.
## [+] Các công cụ: Hardware và Software
- Các máy tính xách tay hoặc máy trạm bổ sung cho mỗi thành viên, tệp nhật ký, thực hiện phân tích dữ liệu và điều tra mà không có bất kỳ hạn chế nào.
- Công cụ phân tích và thu thập hình ảnh pháp y kỹ thuật số
- Công cụ thu thập và phân tích bộ nhớ
- Thu thập và phân tích phản hồi trực tiếp
- Công cụ phân tích nhật ký
- Công cụ thu thập và phân tích mạng 
- Cáp mạng và switch 
- Ổ cứng cho hình ảnh pháp y
- Dây cáp điện Tua vít, nhíp và các công cụ liên quan khác để sửa chữa hoặc tháo rời các thiết bị phần cứng nếu cần
- Người tạo chỉ số Thỏa hiệp (IOC) và khả năng tìm kiếm IOC trong toàn tổ chức 
- Chuỗi biểu mẫu quyền giám hộ 
- Phần mềm mã hóa 
- Đơn theo dõi hệ thống
- Cơ sở an toàn để lưu trữ và điều tra 
- Hệ thống xử lý sự cố độc lập với cơ sở hạ tầng của tổ chức bạn

> Những công cụ trên được gói gọn trong **jump bag** có thể ngay lập tức mang đi và sử dụng.

```
What should we have prepared and always ready to 'grab and go'?
=>  jump bag

True or False: Using baselines, we can discover deviations from the golden image, which aids us in discovering suspicious or unwanted changes to the configuration.
=>  True
```
# Preparation Stage Part 2
---
Sau khi thiết lập các chức năng xử lí sự cố là bảo vệ khỏi sự cố. Một số biện pháp được khuyến nghị cao giảm thiếu tác động của các mối đe dọa.

## DMARC
[DMARC](https://dmarcly.com/blog/how-to-implement-dmarc-dkim-spf-to-stop-email-spoofing-phishing-the-definitive-guide#what-is-dmarc) là một bộ bảo vệ chống lừa đảo email được xây dựng trên [SPF](https://dmarcly.com/blog/how-to-implement-dmarc-dkim-spf-to-stop-email-spoofing-phishing-the-definitive-guide#what-is-spf) và [DKIM](https://dmarcly.com/blog/how-to-implement-dmarc-dkim-spf-to-stop-email-spoofing-phishing-the-definitive-guide#what-is-dkim). DMARC sẽ từ chối các email nghi ngờ độc hại trước khi chúng đến tay bạn. Tuy nhiên sẽ có một số email không độc hại bị loại bỏ nhầm.

## Endpoint Hardening (& EDR)
Các thiết bị cuối là điểm cuối truy cập của các cuộc tấn công mạng. Hiện tại có một số tiêu chẩun tăng cường thiết bị cuối như CIS và Microsoft baselines.Một số hành động quan trọng cần lưu ý và thực hiện là:
- Vô hiệu hóa LLMNR/NetBIOS
- Triển khai LAPS và xóa đặc quyền quản trị của người dùng thông thường
- Tắt hoặc định dạng cấu hình PowerShell ở chế độ "ConstrainedLanguage"
- Kích hoạt Attack Surface Reduction (ASR) khi sử dụng Win defend
- Sử dụng tường lửa dựa trên máy chủ. Ở mức tối thiểu, hãy chặn liên lạc giữa máy trạm với máy trạm và chặn lưu lượng truy cập đi tới LOLbins
- Triển khai một sản phẩm EDR. Tại thời điểm này, AMSI cung cấp khả năng hiển thị tuyệt vời về các tập lệnh bị xáo trộn cho các sản phẩm chống phần mềm độc hại để kiểm tra nội dung trước khi nó được thực thi. Chúng tôi khuyên bạn chỉ nên chọn những sản phẩm tích hợp với AMSI.

## Network Protection
**Network segmentation:** là một kỹ thuật mạnh mẽ để tránh xảy ra vi phạm lan rộng trên toàn bộ tổ chức. Các hệ thống quan trọng trong kinh doanh phải được cách ly và chỉ được phép kết nối khi doanh nghiệp yêu cầu. Tài nguyên nội bộ thực sự không nên đối mặt trực tiếp với Internet (trừ khi được đặt trong DMZ).

Hệ thống IDS/IPS có khả năng chống lại SSL/TLS để xác định lưu lượng truy cập độc hại dựa trên nội dung mạng, chứ không phải đại chỉ của IP.

Đảm bảo rằng chỉ những thiết bị được tổ chức phê duyệt mới có thể truy cập mạng.

## Privilege Identity Management / MFA / Passwords
Tại thời điểm này, việc đánh cắp thông tin xác thực đặc quyền của người dùng là con đường leo thang phổ biến nhất trong môi trường Active Directory. 

Ngoài ra, một lỗi phổ biến là người dùng quản trị viên có mật khẩu yếu (nhưng thường phức tạp) hoặc mật khẩu dùng chung với tài khoản người dùng thông thường của họ (có thể lấy được thông qua nhiều vectơ tấn công như keylogging). 

Để tham khảo, mật khẩu yếu nhưng phức tạp (_weak but complex_) là "Password1!". Nó bao gồm chữ hoa, chữ thường, số và ký tự đặc biệt, nhưng mặc dù vậy, nó vẫn dễ dàng dự đoán được và có thể tìm thấy trong nhiều danh sách mật khẩu mà kẻ thù sử dụng trong các cuộc tấn công của chúng. Nên dạy nhân viên sử dụng các cụm từ mật khẩu vì chúng khó đoán hơn và khó sử dụng vũ lực hơn

## Vulnerability Scanning

Thực hiện quét lỗ hổng liên tục trong môi trường của bạn và khắc phục ít nhất các lỗ hổng "cao" và "nghiêm trọng" được phát hiện. Mặc dù quá trình quét có thể được tự động hóa nhưng việc sửa lỗi thường yêu cầu sự tham gia thủ công. Nếu bạn không thể áp dụng các bản vá vì lý do nào đó, hãy phân chia các hệ thống dễ bị tấn công!

## User Awareness Training

Việc đào tạo người dùng nhận biết hành vi đáng ngờ và báo cáo hành vi đó khi bị phát hiện là một thắng lợi lớn đối với chúng tôi. Mặc dù khó có thể đạt được thành công 100% trong nhiệm vụ này nhưng những khóa đào tạo này được biết là có thể làm giảm đáng kể số lượng thỏa hiệp thành công. Việc kiểm tra "bất ngờ" định kỳ cũng phải là một phần của khóa đào tạo này, chẳng hạn như email lừa đảo hàng tháng, thẻ USB bị đánh rơi trong tòa nhà văn phòng, v.v.
## Active Directory Security Assessment
Cách phát hiện lỗ hổng tốt nhất là tìm kiếm chúng từ góc độ của kẻ tấn công. Việc thực hiện đánh giá của riêng bạn (hoặc thuê bên thứ ba nếu tổ chức thiếu bộ kỹ năng) sẽ đảm bảo rằng khi thiết bị đầu cuối bị xâm phạm, kẻ tấn công sẽ không có khả năng leo thang một bước lên các đặc quyền cao trên mạng. Kẻ tấn công càng tạo ra nhiều công cụ và hoạt động bổ sung thì khả năng bạn phát hiện ra chúng càng cao, vì vậy hãy cố gắng loại bỏ những chiến thắng dễ dàng và những kết quả dễ dàng càng nhiều càng tốt.
## Purple Team Exercises
Chúng ta cần đào tạo những người xử lý sự cố và thu hút họ tham gia. Không có nghi ngờ gì về điều đó, và nơi tốt nhất để làm điều đó là trong môi trường của chính tổ chức. Các bài tập của đội tím về cơ bản là các đánh giá bảo mật do đội đỏ thực hiện liên tục hoặc cuối cùng thông báo cho đội xanh về hành động, phát hiện của họ, bất kỳ thiếu sót nào về khả năng hiển thị/bảo mật, v.v. Các bài tập như vậy sẽ giúp xác định các lỗ hổng trong tổ chức trong khi kiểm tra khả năng phòng thủ của đội xanh khả năng về ghi nhật ký, giám sát, phát hiện và phản hồi.

```
What can we use to block phishing emails pretending to originate from our mail server?
=> DMARC

True or False: "Summer2021!" is a complex password.
=> True
```
