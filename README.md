# HACKATHONCTF-2
LINK BÀI LAB:
https://www.vulnhub.com/entry/hackathonctf-2,714/

Tiến hành Scan:

![image](https://user-images.githubusercontent.com/72652376/125218808-ddb9cd00-e2ed-11eb-8b65-c280f72289d8.png)

Có thể thấy 2 cổng 21(FTP) và 80(HTTP) được mở. Scan kỹ hơn để xem thu được gì không ???

nmap -T4 -sC -sV -p- --min-rate=1000 -oN nmap.log 192.168.1.4
Giải thích thông số:

-T4:timing template (set được từ 0-5, càng cao thì tốc độ càng nhanh)

-sC:tương đương với --script = default

-sV:Thăm dò các cổng đang mở để xác định thông tin dịch vụ / phiên bản 

-p-:Scan port đặc biệt

--min-rate=1000:Kiểm soát trực tiếp tốc độ quét

-oN nmap.log:output được chuyển tiếp đến nmap.log


![image](https://user-images.githubusercontent.com/72652376/125222885-08f3ea80-e2f5-11eb-9917-9ae1d2e2c04a.png)


![image](https://user-images.githubusercontent.com/72652376/125220145-676a9a00-e2f0-11eb-8278-1213491437fb.png)

Scan bằng gobuster để tìm thư mục ẩn, nhưng lại không thu được gì

Bắt đầu tiến hành explot:
Vsftpd 3.0.3 có thể cho đăng nhập bằng tài khoản anonymous 

![image](https://user-images.githubusercontent.com/72652376/125220511-14451700-e2f1-11eb-9bf2-cd625e092481.png)

Get 2 file về máy thu được một flag1 và wordlist(có thể mật khẩu để đăng nhập)

![image](https://user-images.githubusercontent.com/72652376/125220630-40f92e80-e2f1-11eb-923d-717265de9c7e.png)

![image](https://user-images.githubusercontent.com/72652376/125220648-4b1b2d00-e2f1-11eb-92ba-d1da0de1a75f.png)

Tiến hành scan dir lại với tệp word.dir vừa thu được:

![image](https://user-images.githubusercontent.com/72652376/125221517-7eaa8700-e2f2-11eb-8cf7-b83733473c2c.png)

![image](https://user-images.githubusercontent.com/72652376/125221555-8e29d000-e2f2-11eb-95c0-c8d3c23293e1.png)

![image](https://user-images.githubusercontent.com/72652376/125221585-9bdf5580-e2f2-11eb-9f03-fd1168e9ba5e.png)

Thu được username có thể là user đăng nhập SSH

Tiến hành burce force với wordlist thu được bằng hydra:
hydra -V -l hackathonll -P word.dir 192.168.1.4 ssh -s 7223

Giải thích thông số:

-V: hiển thị chi tiết từng lần đăng nhập

-l:tên user cụ thể

-P: tập wordlist password

-s: port đặc biệt khác với port mặc định


![image](https://user-images.githubusercontent.com/72652376/125223282-b404a400-e2f5-11eb-8662-3368aaa8af3e.png)

GOOD...!

![image](https://user-images.githubusercontent.com/72652376/125223469-0776f200-e2f6-11eb-890f-78581df6bb7c.png)

Login SSH thành công, tiến hành up root:

![image](https://user-images.githubusercontent.com/72652376/125223832-9f74db80-e2f6-11eb-8a52-c8f518d13341.png)

Dựa vào các quyền được phân có thể tìm được cách up root trên https://gtfobins.github.io/

![image](https://user-images.githubusercontent.com/72652376/125223957-d1863d80-e2f6-11eb-9309-8af4688413e4.png)


![image](https://user-images.githubusercontent.com/72652376/125223932-c7fcd580-e2f6-11eb-891b-4f02f37ecc46.png)

Up root thành công, tìm cờ

![image](https://user-images.githubusercontent.com/72652376/125224111-25912200-e2f7-11eb-8987-9d86995d7895.png)

DONE!!!


#kid_glitch
#https://explainshell.com/
