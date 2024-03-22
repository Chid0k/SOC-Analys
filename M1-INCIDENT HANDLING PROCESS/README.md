# INCIDENT HANDING
---
> **Xử lí sự cố:** Incident Handling (IH) là một phần quan trọng trong khả năng phòng thủ (_Defensive_) của tổ chức. Các biện pháp bảo vệ triển khai để giảm thiểu rủi ro nhất nhưng cũng không thể thiếu khả năng xử lí sự cố cho những tình huống xấu xảy ra.

## TERMS
1. **EVENT:** là một hành động (action) xảy ra trong một hệ thống hoặc một mạng.
    Example:
    *   Một người dùng gửi mail (sending an email)
    *   Một click chuột (mouse click)
    *   Tường lửa (Fire wall) cho phép yêu cầu kết nối
2. **INCIDENT:** là sự cố, một **event** diễn ra với kết quả xấu. Một ví dụ cho sự cố là _System Crash_ ,hoặc truy cập trái phép dữ liệu (_Unauthorized access_). Không có định nghĩa duy nhất về IH.
    Example:
    *   Mất cắp dữ liệu (data theft)
    *   Mất tiền (funds theft)
    *   Truy cập trái phép hệ thống
    *   Cài đặt và sử dụng phần mềm độc hại (_Malware_) và các công cụ truy cập từ xa không phép.

>**IH (Incident handling)** là tập hợp các quy trình rõ ràng để _quản lý_ (**manage**) và _ứng phó_ (**respond**) với các sự cố bảo mật trong môi truowngf máy tính hoặc một mạng

Sự cố không chỉ bao gồm các Sự cố xâm nhập (_intrusion incidents_) mà bao gồm nhiều loại sự cố như Nội gián độc hại (_malicious insiders_), tính khả dụng (_availability issues_).

DOCUMENT: [Computer Security Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)

## CYBER KILL CHAIN

**Cyber kill chain (a.k.a Attack lifecycle):** bao gồm 7 giai đoạn khác nhau. Được mô tả cách mà một cuộc tấn công diễn ra. 

![img](https://academy.hackthebox.com/storage/modules/148/Cyber_kill_chain.png)

1. **Recon:** Giai đoạn **record** là giai đoạn các kẻ tấn công chọn mục tiêu. Sau đó các kẻ tấn công thực hiện Thu thập thông tin (_performs information gathering_) như dữ liệu người dừng, ứng dụng diệt viruts được sử dụng, OS, network tech,....

2. **Weaponize:** Ở giai đoạn này các phần mềm độc hại (_malware_) được phát triển và giấu trong một số loại Exploit hoặc Payload. Malware được phát triển cực kì nhẹ và không thể dò tìm bằng ứng dụng diệt viruts. 
    > Mục đích của giai đoạn này là: Cung cấp quyền truy cập máy từ xa để triển khai các công cụ cho giai đoạn tiếp theo.

3. **Deliver:** các _malware_ được truyền tải tới các mục tiêu (_victims_).
- Các cách tiếp cận truyền thống như một email hay liên kết tới 1 trang web. Một số kẻ tấn công gọi điện thuyết phục mục tiêu tải _malware_ với lý do kỹ thuật. 
- Hoặc thông qua USB hay các thiết bị phần cứng cố tình để lại.
- Các _malware_ thường yêu câu thực hiện không nhiều hơn 2 click chuột (hoặc _double click_) như chạy tập lệnh thực thi _exce_. 

4. **Exploit:** là thời điểm eploxit hay payload được kích hoạt.
    >Trong giai đoạn này các kẻ tấn công sẽ cố gắng thực thi mã trên hệ thống để dánh sự kiếm soát mục tiêu.

5. **Installation:** đây là giai đoạn _malware_ đang được chạy trên máy tính bị xâm nhập. Một số kỹ thuật được sử dụng phổ biến trong giai đoạn này là:
    * **Dropper**: là một đoạn mã nhỏ được thiết kế cài đặt phần mềm độc hại vào hệ thống.
    * **Backdoors**: Một loại _malware_ được thiết kế để nhưxng kẻ tân công truy cập liên tục vào hệ thống bị xâm nhập.
    * **Rootkits**: Là một phần mềm nhằm mục đích che dấu sự hiện diện của chúng trên hệ thống, tránh sự phát hiện của phần mềm diệt viruts hay các công cụ bảo mật.

6. **Command and control:** Ở giai đoạn này kẻ tấn công thiết lập khả năng truy cập máy tính từ xa vào máy bị xâm nhập. 
7. **Action:** Là giai đoạn cuối cùng mà kẻ tấn công thực hiện nhằm nhiều mục đích khác nhau: Lấy cắp dữ liệu bí mật, leo quyền truy cập cao nhất của một mạng để triển khai Ransomware (một loại mã độc tống tiền).

 > **Mục tiêu: Ngăn chặn kẻ tấn công đi xa nhất trong một chuỗi tấn công.**

```
In which stage of the cyber kill chain is malware developed?
=> Weaponize
```




