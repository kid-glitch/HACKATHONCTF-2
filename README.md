# HACKATHONCTF-2
LINK BÀI LAB:
https://www.vulnhub.com/entry/hackathonctf-2,714/

Tiến hành Scan:

![image](https://user-images.githubusercontent.com/72652376/125218808-ddb9cd00-e2ed-11eb-8b65-c280f72289d8.png)

Có thể thấy 2 cổng 21(FTP) và 80(HTTP) được mở. Scan kỹ hơn để xem thu được gì không ???

![image](https://user-images.githubusercontent.com/72652376/125218918-19549700-e2ee-11eb-908e-16e31868a146.png)

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

Thu được username chưa rõ để làm gì :v 
