# Penetration Testing Overview
---
Kiểm thử thâm nhập (Pentest) là một nỗ lực tấn công có tổ chức, có mục tiêu và được ủy quyền để kiểm tra cơ sở hạ tầng CNTT và các biện pháp bảo vệ cơ sở hạ tầng CNTT nhằm xác định mức độ nhạy cảm của chúng đối với các lỗ hổng bảo mật CNTT. 

Pentest sử dụng các phương pháp và kỹ thuật mà những kẻ tấn công thực sự sử dụng. Với tư cách là người kiểm tra thâm nhập, chúng tôi áp dụng nhiều kỹ thuật và phân tích khác nhau để đánh giá tác động mà một lỗ hổng hoặc chuỗi lỗ hổng cụ thể có thể gây ra đối với tính bảo mật, tính toàn vẹn và tính khả dụng của hệ thống CNTT và dữ liệu của tổ chức.

> **Pentest** nhằm mục đích phát hiện và xác định **TẤT CẢ** các _lỗ hổng_ trong hệ thống đang được điều tra và cải thiện tính bảo mật cho các hệ thống được thử nghiệm.
### Risk Management - Quản lý rủi ro
* Mục tiêu chính của **Risk Management** là xác định, đánh giá và giảm thiểu mọi rủi ro tiềm ẩn có thể gây tổn hại đến tính bảo mật, tính toàn vẹn và tính sẵn có của hệ thống thông tin và dữ liệu của tổ chức, đồng thời giảm rủi ro tổng thể xuống mức có thể chấp nhận được.
* Điều này bao gồm việc xác định các mối đe dọa tiềm ẩn, đánh giá rủi ro và thực hiện các bước cần thiết để giảm thiểu hoặc loại bỏ chúng.
* Tuy nhiên, không thể loại bỏ hết mọi rủi ro. Vẫn tồn tại tính chất của rủi ro tiềm ẩn một cuộc xâm nhập an ninh, ngay cả khi tổ chức đã thực hiện tất cả các biện pháp hợp lý để quản lý rủi ro. Do đó, một số rủi ro sẽ tiếp tục tồn tại. Rủi ro tiềm ẩn là mức độ rủi ro mặc dù các biện pháp kiểm soát an ninh thích hợp đã được thiết lập. Công ty có thể chấp nhận, chuyển giao, tránh và giảm thiểu các rủi ro theo nhiều cách khác nhau.
### Vulnerability Assessments - Đánh giá khả năng dễ bị xâm nhập
**Vulnerability analysis** là một khái niệm chung bao gồm Đánh giá lỗ hổng hoặc bảo mật (_vulnerability or security assessments_) và Kiểm thử xâm nhập (_penetration tests_). Hệ thống được kiểm tra các sự cố đã biết và lỗ hổng bảo mật bằng cách chạy các công cụ quét như Nessus, Qualys, OpenVAS,... Trong hầu hết các trường hợp, các bước kiểm tra tự động này không thể điều chỉnh các cuộc tấn công theo cấu hình của hệ thống đích.
* Pentest là sự kết hợp giữa kiểm tra/xác nhận tự động và thủ công và được thực hiện sau khi thu thập thông tin thủ công, trong hầu hết các trường hợp. Nó được thiết kế và điều chỉnh riêng cho hệ thống đang được thử nghiệm.
* Điều này là do các thử nghiệm và hoạt động riêng lẻ được thực hiện trong quá trình pentest có thể bị coi là tội hình sự nếu người thử nghiệm không có văn bản ủy quyền rõ ràng để tấn công hệ thống của khách hàng. Tổ chức thực hiện thử nghiệm thâm nhập chỉ có thể yêu cầu thử nghiệm đối với tài sản của chính mình. Nếu họ đang sử dụng bất kỳ bên thứ ba nào để lưu trữ trang web hoặc cơ sở hạ tầng khác, họ cần phải có được sự chấp thuận rõ ràng bằng văn bản từ các tổ chức này trong hầu hết các trường hợp.
* Một cuộc pentest thành công đòi hỏi sự tổ chức và chuẩn bị đáng kể. Phải có một mô hình quy trình đơn giản mà chúng tôi có thể làm theo, đồng thời, thích ứng với nhu cầu của khách hàng, vì mọi môi trường chúng tôi gặp sẽ khác nhau và có những sắc thái riêng.


## [+] Testing Methods
Mỗi pentest có thể được thực hiện từ hai quan điểm khác nhau: 
* External or Internal
### 1.  External Penetration Test
* Nhiều cuộc pentest được thực hiện từ góc độ bên ngoài hoặc với tư cách là người dùng ẩn danh trên Internet. 
* Hầu hết khách hàng muốn đảm bảo rằng họ được bảo vệ tốt nhất có thể trước các cuộc tấn công vào phạm vi mạng bên ngoài của họ. 
* Chúng tôi có thể thực hiện kiểm tra từ máy chủ của chính mình (hy vọng sử dụng kết nối VPN để tránh ISP chặn chúng tôi) hoặc từ VPS. 
* Một số khách hàng sẽ không quan tâm đến việc tàng hình, trong khi những khách hàng khác sẽ yêu cầu chúng tôi tiến hành càng lặng lẽ càng tốt và tiếp cận các hệ thống mục tiêu để tránh bị tường lửa và hệ thống IDS/IPS cấm cũng như tránh kích hoạt cảnh báo.
>Cuối cùng, mục tiêu của chúng tôi ở đây là:  truy cập vào các máy chủ bên ngoài, lấy dữ liệu nhạy cảm hoặc giành quyền truy cập vào mạng nội bộ.
### 2.  Internal Penetration Test
Ngược lại với pentest bên ngoài, pentest nội bộ là khi chúng tôi thực hiện kiểm tra từ bên trong mạng công ty. Giai đoạn này có thể được thực thi sau khi xâm nhập thành công vào mạng công ty thông qua pentest bên ngoài hoặc bắt đầu từ một tình huống vi phạm giả định. Các cuộc thử nghiệm nội bộ cũng có thể truy cập vào các hệ thống biệt lập không có quyền truy cập Internet, điều này thường yêu cầu sự hiện diện thực tế của chúng tôi tại cơ sở của khách hàng.
## [+] Types of Penetration Testing
Dựa vào lượng thông tin được cung cấp, có các loại pentest như sau:
|      Type      | Information Provided                                                                                                 |
|:--------------:|----------------------------------------------------------------------------------------------------------------------|
| Blackbox       | Minimal. Chỉ những thông tin cần thiết như địa chỉ IP hoặc tên miền                                                  |
| Greybox        | Extended. Thêm những thông tin URL cụ thể, tên máy chủ, mạng con.                                                    |
| Whitebox       | Maximun. Tất cả những gì có thể có như cấu hình chi tiết, thông tin đăng nhập quản trị, mã nguồn ứng dụng, web       |
| Red-Teaming    | Có thể bao gồm thử nghiệm vật lý và kỹ thuật xã hội, cùng những thứ khác. Có thể kết hợp với bất kỳ loại nào ở trên. |
| Purple-Teaming | Nó có thể được kết hợp với bất kỳ loại nào ở trên. Tuy nhiên, nó tập trung vào việc hợp tác chặt chẽ với Defeneder . |

Chúng tôi càng được cung cấp ít thông tin thì cách tiếp cận sẽ càng mất nhiều thời gian và phức tạp hơn. Kiểu trinh sát này có thể mất một khoảng thời gian đáng kể, đặc biệt nếu khách hàng yêu cầu một cách tiếp cận lén lút hơn để thử nghiệm.
## [+] Types of Testing Environments
Ngoài phương pháp thử nghiệm và loại thử nghiệm, một vấn đề cần cân nhắc khác là những gì sẽ được thử nghiệm, có thể được tóm tắt trong các loại sau:
| Network | Web App | Mobile            | API               | Thick Clients |
|---------|---------|-------------------|-------------------|---------------|
| IoT     | Cloud   | Source Code       | Physical Security | Employees     |
| Hosts   | Server  | Security Policies | Firewalls         | IDS/IPS       |



# Laws and Regulations
---
DOCUMENT: [Search](https://www.google.com.vn/)
# Penetration Testing Process
---

![Penetration Testing Stages](https://academy.hackthebox.com/storage/modules/90/0-PT-Process.png)
Cần phân biệt giữa quá trình **deterministic** (quyết định) và **stochastic** (ngẫu nhiên). 

**Deterministic process** là quá trình mà mỗi giai đoạn phụ thuộc và xác định bởi giai đoạn (_stage_) và sự kiện (_event_) trước. 

**Stochastic process**  là một trong những trạng thái chỉ theo sau các trạng thái khác với 1 xác suất nhất định. (_A stochastic process is one in which one state follows from other states only with a certain probability_).

**Penetration Testing Process** được xác định bởi: các bước (_stage_) và sự kiện liên tiếp (_event_) được thực hiện bởi Tester để tìm đường dẫn tới mục tiêu xác đinhk trước.

## [+] Penetration Testing Stages
### 1.  Pre-Engagement
Toàn bộ quá trình trước khi tham gia bao gồm ba thành phần thiết yếu:
- Bảng câu hỏi xác định phạm vi (_Scoping questionnaire_)
- Pre-engagement meeting
- Kick-off meeting

Before any of these can be discussed in detail, a **Non-Disclosure Agreement (NDA)** must be signed by all parties. There are several types of NDAs:

| Type             | Description                                                                                                                                                                                             |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Unilateral NDA   | This type of NDA obligates only one party to maintain confidentiality and allows the other party to share the information received with third parties.                                                  |
| Bilateral NDA    | In this type, both parties are obligated to keep the resulting and acquired information confidential. This is the most common type of NDA that protects the work of penetration testers.                |
| Multilateral NDA | Multilateral NDA is a commitment to confidentiality by more than two parties. If we conduct a penetration test for a cooperative network, all parties responsible and involved must sign this document. |

Giai đoạn này cũng yêu cầu chuẩn bị một số tài liệu trước khi tiến hành thử nghiệm thâm nhập. Tài liệu này phải có chữ ký của khách hàng và chúng tôi để tuyên bố đồng ý cũng có thể được trình bày dưới dạng văn bản nếu được yêu cầu:

| Document                                                       | Timing for Creation                             |
|----------------------------------------------------------------|-------------------------------------------------|
| 1. Non-Disclosure Agreement (NDA)                              | After Initial Contact                           |
| 2. Scoping Questionnaire                                       | Before the Pre-Engagement Meeting               |
| 3. Scoping Document                                            | During the Pre-Engagement Meeting               |
| 4. Penetration Testing Proposal (Contract/Scope of Work (SoW)) | During the Pre-engagement Meeting               |
| 5. Rules of Engagement (RoE)                                   | Before the Kick-Off Meeting                     |
| 6. Contractors Agreement (Physical Assessments)                | Before the Kick-Off Meeting                     |
| 7. Reports                                                     | During and after the conducted Penetration Test |

>**Warning**: These documents should be reviewed and adapted by a lawyer after they have been prepared.



### 2.  Vulnerability Assessment
## [+] Importance

| Stage                       | Description                                                                                                                                                                                                                                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. Pre-Engagement           | The first step is to create all the necessary documents in the pre-engagement phase, discuss the assessment objectives, and clarify any questions.                                                                                                                                         |
| 2. Information Gathering    | Once the pre-engagement activities are complete, we investigate the company's existing website we have been assigned to assess. We identify the technologies in use and learn how the web application functions.                                                                           |
| 3. Vulnerability Assessment | With this information, we can look for known vulnerabilities and investigate questionable features that may allow for unintended actions.                                                                                                                                                  |
| 4. Exploitation             | Once we have found potential vulnerabilities, we prepare our exploit code, tools, and environment and test the webserver for these potential vulnerabilities.                                                                                                                              |
| 5. Post-Exploitation        | Once we have successfully exploited the target, we jump into information gathering and examine the webserver from the inside. If we find sensitive information during this stage, we try to escalate our privileges (depending on the system and configurations).                          |
| 6. Lateral Movement         | If other servers and hosts in the internal network are in scope, we then try to move through the network and access other hosts and servers using the information we have gathered.                                                                                                        |
| 7. Proof-of-Concept         | We create a proof-of-concept that proves that these vulnerabilities exist and potentially even automate the individual steps that trigger these vulnerabilities.                                                                                                                           |
| 8. Post-Engagement          | Finally, the documentation is completed and presented to our client as a formal report deliverable. Afterward, we may hold a report walkthrough meeting to clarify anything about our testing or results and provide any needed support to personnel tasked with remediating our findings. |




