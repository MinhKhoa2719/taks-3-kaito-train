# taks-3-kaito-train

- Docker là gì? ưu điểm nhược điểm ?
- Cài đặt Docker trên môi trường window/linux/vscode (linux sử dụng wsl2 trên window)
- Demo

Task 3

- Docker là một dự án mã nguồn mở giúp tự động triển khai các ứng dụng Linux và Window vào trong các container ảo hóa,
- Docker là một công cụ giúp cho việc tạo ra và triển khai các container để phát triển, chạy ứng dụng được dễ dàng. Các container là môi trường, mà ở đó lập trình viên đưa vào các thành phần cần thiết để ứng dụng của họ chạy được, bằng cách đóng gói ứng dụng cùng với container như vậy, nó đảm bảo ứng dụng chạy được và giống nhau ở các máy khác nhau (Linux, Windows, Desktop, Server ...)
- Docker mang lại lợi ích cho cả lập trình viên lẫn quản trị hệ thống, sử dụng Docker lập trình viên tập trung vào mà viết code chứ không lo lắng về việc triển khai, không lo lắng ở máy của lập trình viên chạy được, máy khác lại không chạy được ...

- Docker cung cấp một lớp trừu tượng và tự động ảo hóa dựa trên linux. 
- Docker sử dụng những tài nguyên cô lập của linux như cgroup,kernel. quản lý têp để cho 
- phép các container chạy độc lập bên trong một thực thể linux

Là nền tảng để cung cấp cách để building, deploying và running ứng dụng dễ dàng hơn bằng cách sử dụng các containers(trên nền tảng ảo hóa). Ban đầu viết bằng 
Python, hiện tại đã chuyển sang Golang

# Ưu điểm của Docker :

- Environment : Gọi nôm na là môi trường xử lý của ứng dụng. ví dụ mình cần môi trường để chạy ứng dụng java, php, python, ….  để chạy 1 site wordpress thì mình phải cài php, - apache. mysql, với Docker thì mình chỉ cần 1 câu lệnh docker run là có ngay môi trường để chạy site wordpress không cần cài đặt gì cả.

- Reduced Risk : Giảm sự cố khi đưa lên production. Mình chỉ cần build, test ok cái image app rồi lên server production pull nó về run là ok.

- Portability across machines :  Ứng dụng và tất cả các thành phần cần thiết để run ứng dụng đó mình chỉ cần build nó nằm trong 1 container,  Sau đó mình có thể share  hoặc là chuyển nó tới bất kỳ hệ thống nào có chạy docker engine là nó chạy mướt luôn, không có lỗi gì.

- Scale :  Khi mà 1 app nó đang thiếu resource thì mình chỉ cần ghỏ lệnh scale nó lên, cái này mình sẽ thấy rỏ trong Docker Swarm Mode


# Nhược điểm
- Nhược điểm của docker là không thể chạy trực tiếp trên Windows và MAC OS. Chính vì thế, khi các bạn sử dụng Docker trên Windows hay MAC OS thì Docker sẽ phải run một máy ảo linux rồi mới có thể thực thi được.

- Không phải app nào củng containerized được.

- Container nó sài shared OS kernel Linux nên nếu có vấn đề gì ảnh hưởng tới OS kernel của Node thì nó củng bị ảnh hưởng.

- Số lượng container càng lớn thì càng phức tạp.

- Phải follow và improve liên tục nếu muốn chạy nó trên production để control được Docker vì nó không có stable ( điều này là dĩ nhiên vì đây là open source )

# Container trong Docker

- Các container cho phép lập trình viên đóng gói một ứng dụng với tất cả các phần cần thiết,chẳng hạn như thư viện và các phụ thuốc khác và gói tất cả ra dưới 

dạng một package

- Bằng cách đó, nhờ vào container, ứng dụng sẽ chạy trên mọi máy Linux khác bất kể mọi cài đặt tùy chỉnh mà máy có thể có khác với máy được sử dụng để viết 

ccode,

- Theo một cách nào đó ,Docker khá giống với virtual machine,Nhưng nguyên nhân mà Docker Phát triển là do:

# Tính dễ ứng dụng:
- Rất dễ cho mọi người sử dụng từ lập trình viên,sys admin...

nó tận dụng lợi thế của container để build, test nhanh chóng,có thể đóng gói ứng dụng trên laptop của họ và chạy trên public cloud,private cloud...

- Câu thần chú là "Build once,run anywhere".

# Docker container rất nhẹ và nhanh:
- Bạn có thể tạo và chạy docker container trong vài giây

#Môi trường chạy và khả năng mở rộng: 
- Bạn có thể chia nhỏ những chức năng của ứng dụng thành các container riêng lẻ . 

- Ví dụ trong database chạy trên một container và redis cache có thể chạy trên một container khác trong khi ứng dụng Node.js lại chạy trên một cái khác nữa 

- Với docker rất dễ để liên kết các container với nhau để tạo thành một ứng dụng, làm cho nó dễ dàng scale,update các thành phần độc lập với nhau.

- Là thành phần quan trọng trong một phần của devops


- Các khái niệm liên quan


![1](https://user-images.githubusercontent.com/54676091/91885401-e5fab200-ecb1-11ea-9c34-cc8ae31fb207.png)

- Docker Engine : là thành phần chính của Docker, như một công cụ để đóng gói ứng dụng

- Docker Hub : là một “github for docker images”. Trên DockerHub có hàng ngàn public images được tạo bởi cộng đồng cho phép bạn dễ dàng tìm thấy những image mà bạn cần. Và chỉ cần pull về và sử dụng với một số config mà bạn mong muốn..

- Images: là một khuôn mẫu để tạo một container. Thường thì image sẽ dựa trên 1 image có sẵn với những tùy chỉnh thêm. Ví dụ bạn build 1 image dựa trên image Centos mẫu có sẵn để chạy Nginx và những tùy chỉnh, cấu hình để ứng dụng web của bạn có thể chạy được. Bạn có thể tự build một image riêng cho mình hoặc sử dụng những image được chia sẽ từ cộng đồng Docker Hub. Một image sẽ được build dựa trên những chỉ dẫn của Dockerfile.

- Container: là một instance của một image. Bạn có thể create, start, stop, move or delete container dựa trên Docker API hoặc Docker CLI.
- Docker Client: là một công cụ giúp người dùng giao tiếp với Docker host.
- Docker Daemon: lắng nghe các yêu cầu từ Docker Client để quản lý các đối tượng như Container, Image, Network và Volumes thông qua REST API. Các Docker Daemon cũng giao tiếp với nhau để quản lý các Docker Service.
- Dockerfile: là một tập tin bao gồm các chỉ dẫn để build một image .
- Volumes: là phần dữ liệu được tạo ra khi container được khởi tạo.
*Ngoài ra còn nhiều khái niệm nữa như swarm, compose…
.
# Quy trình thực thi của một hệ thống sử dụng Docker

![2](https://user-images.githubusercontent.com/54676091/91886016-e3e52300-ecb2-11ea-9dd2-c7b0bdfaae86.png)

# Như trong hình vẽ, một hệ thống Docker được thực thi với 3 bước chính :
- Build -> Push -> Pull,Run

# Build
- Đầu tiên tạo một dockerfile, trong dockerfile này chính là code của chúng ta. Dockerfile này sẽ được Build tại một máy tính đã cài đặt Docker Engine. Sau khi build ta sẽ có được Container, trong Container này chứa ứng dụng kèm bộ thư viện của chúng ta.
# Push
- Sau khi có được Container, chúng ta thực hiện push Container này lên cloud và lưu tại đó.

# Pull, Run
- Nếu một máy tính khác muốn sử dụng Container chúng ta thì bắt buộc máy phải thực hiện việc Pull container này về máy, tất nhiên máy này cũng phải cài Docker Engine. Sau đó thực hiện Run Container này.

# .
# Vậy khi nào sử dụng Docker?

- Triển khai kiến trúc Microservices.
- Khi xây dựng ứng dụng và cần scale một cách linh hoạt.
- Khi bạn muốn không tốn khá nhiều thời gian để config máy local và server cùng một môi trường để chạy được ứng dụng. Bạn chỉ cần build 1 lần chạy ở nhiều nơi mà thôi.
- Sản phẩm của công ty bạn cần một cách tiếp cận mới về xây dựng, đẩy lên server, thực thi ứng dụng một cách nhanh chóng dễ dàng.


# Cài đặt Docker trên môi trường window/linux/vscode (linux sử dụng wsl2 trên window)
_Bổ sung_

# 1 - Cài đặt WSL / WSL2 trên Windows 10 để code như trên Ubuntu
Windows support "cài cả Ubuntu trên Win"

- Một vài cái chính dùng để code trên Ubuntu dự kiến cần setup được trên Win đó là:
- Docker
- Terminal (Konsole)
- ZSH / Fish
- VSCode
- Git
- PHP
- Node.js
- Golang

- Ghé qua trang chủ để tải file cài đặt Docker cho Windows về 

https://www.docker.com/products/docker-desktop.

*mở file cài đặt thì ăn ngay quả message Hyper-V feature is required

Mà cái feature này lại không có trên Windows 10 Home. Quá nhọ! Lại phải cài lại Win và xin ngay quả key cho Windows 10 Enterprise 😄

- Thế nên anh em nào muốn dùng docker trên windows 10 thì phải xem xét điều này trước tiên nhé

# .
Bước tiếp theo sau khi có edition phù hợp, hỗ trợ Hyper-V, mình tiếp tục bật chức năng này lên theo document của Microsoft, vắn tắt lại thì cần làm như sau:

- Kiểm tra câu hình yêu cầu: 64bits, RAM từ 4GB, windows pro hoặc enterprise hoặc - education

- Mở Powershell với quyền Administrator

- Chạy lệnh sau:

*Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All



- Reboot máy là xong
# Hoặc nếu thích dùng UI thì:

- Window + R, nhập Control để vào Control Panel
- Chọn Programs, ở mục Programs and Features chọn Turn Windows feature on or off
- Hộp thoại xuất hiện thì tích chọn Hyper-V, lưu lại rồi reboot là xong

![2](https://user-images.githubusercontent.com/54676091/92068118-3e27d600-edd0-11ea-8a46-f901f0010258.png)


Sau khi reboot, bật Docker lên và cuối cùng nó cũng đã chạy.
Mình thử chạy vài lệnh với docker trên Powershell để kiểm tra và mọi thứ đã OK.

*docker info
*docker ps


# -------------------------------------------------------------

# Cài đặt WSL + cấu hình với Docker
Sau khi cài đặt docker thành công
- Cần mang lại Konsole về Windows







