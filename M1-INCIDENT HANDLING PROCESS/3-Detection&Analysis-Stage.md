# Detection & Analysis Stage Part 1
---
Quy trình và thủ tục (_process and procedure_) và hướng dẫn về cách xử lí các sự cố bảo mật.

Các mối đe dọa được gửi đến tổ chức qua nhiều cách và việc phát hiện chúng đến từ nhiều nguồn:
- Nhân viên tổ chức cảnh báo về điều gì đó bất thường
- Cảnh báo từ các công cụ (Firewall, EDR, IDS, ...)
- Hoạt động săn lùng (Threat hunting activities)
- Được thông báo từ một tổ chưcs bên ngoài.

Các cấp độ phát hiện dựa trên mạng cho phép như sau:
- Phát hiện ở mạng lớn (Detection at the network perimeter) EX: using fireware, internet-facing network intrusion detection/prevention systems, ...
- Phát hiện ở cấp độ mạng nội bộ (Detection at the internal network level) EX: using local firewalls, host intrusion detection/prevention systems, ...
- Phát hiện ở cấp độ thiết bị đầu cuối (Detection at the endpoint level) EX: using antivirus systems, endpoint detection & response systems, ...
- Phát hiện ở cấp độ ứng dụng (Detection at the application level) EX: using application logs, service logs, ...

## Initial Investigation - Khảo sát ban đầu
Suy nghĩ về các thông tin trong trường hợp tài khoản quản trị viên kết nối với địa chỉ IP tại thời điểm HH:MM:SS. Nếu không biết hệ thống nào trên địa chỉ IP đó, múi giờ dẫn đến phát hiện sai về EVENT này.

Mục tiêu là thu thập nhiều nhất các thông tin sau:
- Thời gian cụ thể, người đã báo cáo 
- Sự việc được phát hiện như thế nào
- Phân loại sự cố: Lừa đảo, treo hệ thống, ...
- Tập hợp cách danh sách hệ thống, tài nguyên bị ảnh hưởng. Ghi lại những ai đã truy cập vào hệ thống bị ảnh hưởng và đã thực hiện hành động gì.
- Vị trí vật lý, hệ điều hành, tên máy chủ, chủ sở hữu hệ thống, mục đích của hệ thống, trạng thái hiện tại của hệ thống.
- (Nếu có liên quan đến phần mềm độc hại) Danh sách địa chỉ IP, ngày và giờ phát hiện, loại phần mềm độc hại, hệ thống bị ảnh hưởng, xuất các tệp độc hại có thông tin pháp y về chúng (chẳng hạn như hàm băm, bản sao của tệp, v.v.)

Với lượng thông tin như vậy, ta cần lập dòng thời gian sự cố dựa trên thời điểm chúng xảy ra (_time_). Nhìn chung dòng thời gian phải chứa được thông tin như bảng sau: 
|    Date    | Time of event | Host name  | Event description                   | Data source        |
|:----------:|---------------|------------|-------------------------------------|--------------------|
| 22/03/2024 | 14:53 CET     | SQLserver1 | Hacker tool 'Mimikatz' was detected | Antivirus Software |

## Incident Severity & Extent Questions - Câu hỏi về mức độ nghiêm trọng và phạm vi sự cố.
Khi xử lí sự cố bảo mật chúng ta nên tự trả lời các câu hỏi sau để xác định tính nghiêm trọng của vấn đề:
- Exploxitation tác động đến điều gì ?
- Explotation yêu cầu những điều gì ?
- Sự cố có ảnh hưởng đến bất kì hệ thống quan trọng nào trong kinh doanh không
- Có bước khắc phục nào được đề xuất ?
- Có bao nhiêu hệ thống đã bị ảnh hưởng ?
- Việc khai thác lỗ hổng còn diễn ra không ?
- Mã độc có khả năng tự lan truyền nhưu sâu máy tính hay không (khoông cần sự tương tác từ người dùng) ?

Hai điều cuối cho thấy sự tinh vi của kẻ tấn công. 
## Incident Confidentiality & Communication - Bảo mật sự cố và liên lạc.
Sự cố là một sự kiện cần được giữ bí mật ít nhất cho đến khi sự cố được khắc phục vì những kẻ tấn công khác có thể lợi dụng sự cố để tiếp tục thực hiện hành vi tấn công. 

Khi một cuộc điều tra được tiến hành, chúng tôi sẽ đặt ra một số kỳ vọng và mục tiêu. Chúng thường bao gồm loại sự cố đã xảy ra, nguồn bằng chứng mà chúng tôi có sẵn và ước tính sơ bộ về lượng thời gian mà nhóm cần cho việc điều tra. Ngoài ra, dựa trên sự việc, chúng tôi sẽ đặt kỳ vọng về việc liệu chúng tôi có thể phát hiện ra kẻ thù hay không. Tất nhiên, nhiều điều trên có thể thay đổi khi cuộc điều tra tiến triển và những manh mối mới được phát hiện. Điều quan trọng là phải giữ cho mọi người tham gia và ban quản lý được thông báo về bất kỳ tiến bộ và kỳ vọng nào.

```
True or False: Can a third party vendor be a source of detecting a compromise?
=> True
```

# Detection & Analysis Stage Part 2
---
Khi một cuộc điều tra bắt đầu, chúng tôi mong muốn hiểu được chuyện gì đã xảy ra và như thế nào. Nếu chúng tôi không biết sự cố đã xảy ra như thế nào hoặc điều gì đã bị ảnh hưởng thì bất kỳ bước khắc phục nào chúng tôi thực hiện sẽ không đảm bảo rằng kẻ tấn công không thể lặp lại hành động của mình để lấy lại quyền truy cập. Mặt khác, nếu chúng ta biết chính xác cách kẻ thù xâm nhập, công cụ chúng sử dụng và hệ thống nào bị ảnh hưởng thì chúng ta có thể lập kế hoạch khắc phục để đảm bảo rằng đường tấn công này không thể bị lặp lại.

## The Investigation - Điều tra
Cuộc điều tra dựa trên các thông tin được thu thập từ ban đầu. Với những dữ liệu này chúng tôi thực hiện quy trình tuần hoàn 3 bước:
- Tạo và sử dụng các _indicators of compromise_ (IOC)
- Xác định các khách hàng có nguy cơ bị ảnh hưởng.
- Thu thập và phân tích dữ liệu từ khách hành và hệ thống bị ảnh hưởng.

### Initial Investigation Data - Dữ liệu điều tra ban đầu
Các cuộc điều tra phải dựa trên các đầu mối thu thập được trong suốt cả quá trình điều tra. Nhóm IH phải liên tục đưa ra các đầu mối mới và không chỉ theo đuổi 1 phát hiện cục thể. Điều này dẫn đến kết quả hạn chế. kết luận sớm và thiếu hiều biết cho điều tra tổng thể.
### Creation & Usage Of IOCs
Dấu hiệu một sự cho phép (_compromise_) là dấu hiệu cho thấy một sự cố đã xảy ra.IOC được ghi lại có cấu trúc, đại điện cho tạo tác của sự cho phép (_the artifacts of the compromise_). EX: địa chỉ IP, Giá trị mảng băm của tệp, tên tệp. Có một số công cụ miễn phí có thể được sử dụng, chẳng hạn như **IOC Editor của Mandiant**, để tạo hoặc chỉnh sửa IOC. Bằng cách sử dụng những ngôn ngữ này, chúng tôi có thể mô tả và sử dụng các hiện vật mà chúng tôi phát hiện được trong quá trình điều tra sự cố. Chúng tôi thậm chí có thể lấy IOC từ bên thứ ba nếu biết rõ kẻ thù hoặc cuộc tấn công.


Một cách tiếp cận phổ biến là sử dụng WMI hoặc PowerShell cho các hoạt động liên quan đến IOC trong môi trường Windows.

>**Warning**: Trong quá trình điều tra phải hết sức để lộ thông tin đăng nhập của những người dùng có đặc quyền cao (ex: root, admin, ...). khi bị lưu vào bộ đệm khi kết nối tới các hệ thống có khẳ năng bị xâm phạm. Cần đảm bảo giao thức và các công cụ kết nối không lưu thông tin đăng nhập bào bộ đệm.

### Identification Of New Leads & Impacted Systems
Sau khi tìm kiếm IOC, bạn có thể sẽ thấy một số lần truy cập tiết lộ các hệ thống khác có cùng dấu hiệu bị xâm phạm. Những lượt truy cập này có thể không liên quan trực tiếp đến vụ việc mà chúng tôi đang điều tra. 


Trong trường hợp IOC quá chung chung, chúng ta nên ưu tiên những thứ chúng ta sẽ tập trung vào, lý tưởng nhất là những thứ có thể cung cấp cho chúng ta những khách hàng tiềm năng sau khi phân tích pháp y.

### Data Collection & Analysis From The New Leads & Impacted Systems 

Sau khi xác định được các hệ thống bao gồm IOC của mình, chúng tôi sẽ muốn thu thập và lưu giữ trạng thái của các hệ thống đó để phân tích thêm nhằm phát hiện ra các đầu mối mới và/hoặc trả lời các câu hỏi điều tra về vụ việc. Tùy thuộc vào hệ thống, có nhiều cách tiếp cận về cách thức và loại dữ liệu cần thu thập. 

Đôi khi, chúng tôi muốn thực hiện 'phản hồi trực tiếp' trên hệ thống khi nó đang chạy, trong khi trong các trường hợp khác, chúng tôi có thể muốn tắt hệ thống và sau đó thực hiện bất kỳ phân tích nào về hệ thống đó. Phản hồi trực tiếp là cách tiếp cận phổ biến nhất, trong đó chúng tôi thu thập một tập hợp dữ liệu được xác định trước thường có nhiều tạo phẩm có thể giải thích những gì đã xảy ra với hệ thống. Tắt hệ thống không phải là một quyết định dễ dàng khi nói đến việc lưu giữ thông tin có giá trị vì trong nhiều trường hợp, phần lớn thành phần sẽ chỉ tồn tại trong bộ nhớ RAM của máy và bộ nhớ này sẽ bị mất nếu tắt máy. Bất kể chúng tôi chọn phương pháp thu thập nào, điều quan trọng là đảm bảo xảy ra tương tác tối thiểu với hệ thống để tránh làm thay đổi bất kỳ bằng chứng hoặc hiện vật nào.

Khi dữ liệu đã được thu thập, đã đến lúc phân tích nó. Đây thường là quá trình tốn nhiều thời gian nhất khi xảy ra sự cố. Phân tích phần mềm độc hại và điều tra ổ đĩa là những loại kiểm tra phổ biến nhất. Mọi khách hàng tiềm năng mới được phát hiện và xác thực đều được thêm vào dòng thời gian được cập nhật liên tục. Cũng lưu ý rằng điều tra bộ nhớ là một khả năng ngày càng trở nên phổ biến và cực kỳ phù hợp khi xử lý các cuộc tấn công nâng cao.


```
During an investigation, we discovered a malicious file with an MD5 hash value of 'b40f6b2c167239519fcfb2028ab2524a'. How do we usually call such a hash value in investigations? Answer format: Abbreviation
=> IOC / IOCs
```