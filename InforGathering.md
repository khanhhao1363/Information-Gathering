# Information Gathering

> Tài Liệu: HackerOne

> Mục Tiêu: Shopify.com

> Người Thực Hiện: Nguyễn Khánh Hào

> Cập Nhật Lần Cuối: 15/10/2024


# Mục Lục

[Summary](#summary)

[Gathering Information Using Whois Lookup](#gathering-information-using-whois-lookup)

[Discovering Websites On The Same Server](#discovering-websites-on-the-same-server)

[Discovering Subdomains](#discovering-subdomains)

[Discovering Sensitive Files](#discovering-sensitive-file)

[Google Hacking](#google-hacking)

# Summary

Có một câu rất hay trong "Binh Pháp Tôn Tử": "Biết địch biết ta, trăm trận trăm thắng".
Để có thể tấn công hay pentest một thứ gì đó thì thứ chúng ta cần có chính là "thông tin", Do thám (Reconnaissance) chính là bước đầu tiên của một quy trình kiểm thử, đây là công đoạn quan trọng và chiếm phần lớn tỉ lệ thành công của một dự án pentest.

# Gathering Information Using Whois Lookup

Đầu tiên, chúng ta sử dung `nslookup` để biết được ip address của target.

![ảnh](https://github.com/user-attachments/assets/c7f42bcd-4312-4f6b-b653-d0438121f4c8)

Tiến hành sử dụng `whois` để recon sâu hơn về IP và DNS.

![ảnh](https://github.com/user-attachments/assets/d5194d89-d93a-4d64-b852-3857eaee5cd6)

Sau khi chạy tool thì chúng ta có kết quả như sau:

```
NetRange:       23.227.32.0 - 23.227.63.255
CIDR:           23.227.32.0/19
NetName:        SHOPIFY-NET
NetHandle:      NET-23-227-32-0-1
Parent:         NET23 (NET-23-0-0-0-0)
NetType:        Direct Allocation
OriginAS:       AS62679
Organization:   Shopify, Inc. (SHOPI-1)
RegDate:        2013-09-19
Updated:        2021-12-14
Ref:            https://rdap.arin.net/registry/ip/23.227.32.0



OrgName:        Shopify, Inc.
OrgId:          SHOPI-1
Address:        151 O'Connor Street, Ground floor
City:           Ottawa
StateProv:      ON
PostalCode:     K2P 2L8
Country:        CA
RegDate:        2013-07-09
Updated:        2022-10-03
Ref:            https://rdap.arin.net/registry/entity/SHOPI-1


OrgNOCHandle: SHOPI-ARIN
OrgNOCName:   Shopify Operations
OrgNOCPhone:  +1-888-746-7439 
OrgNOCEmail:  ops+arin@shopify.com
OrgNOCRef:    https://rdap.arin.net/registry/entity/SHOPI-ARIN

OrgAbuseHandle: SHOPI2-ARIN
OrgAbuseName:   Shopify Abuse
OrgAbusePhone:  +1-888-746-7439 
OrgAbuseEmail:  abuse@shopify.com
OrgAbuseRef:    https://rdap.arin.net/registry/entity/SHOPI2-ARIN

OrgTechHandle: SHOPI-ARIN
OrgTechName:   Shopify Operations
OrgTechPhone:  +1-888-746-7439 
OrgTechEmail:  ops+arin@shopify.com
OrgTechRef:    https://rdap.arin.net/registry/entity/SHOPI-ARIN
```
Dải IP address được cấp phát từ `23.227.32.0` đến `23.227.63.255`.

Ngày đăng ký dải địa chỉ IP: `2013-09-19`

Tên tổ chức sở hữu dải địa chỉ này là `Shopify, Inc`.

...

# Discovering Websites On The Same Server

Để discovering chúng ta sẽ sử dụng `yougetsignal.com`

![ảnh](https://github.com/user-attachments/assets/17773e19-2bc8-45d0-9b15-a57ff18b3b26)

=> Có 122 domain được host trên server.

# Discovering Subdomains

Để list ra các subdomain, mình sẽ sử dụng `subfinder`

![ảnh](https://github.com/user-attachments/assets/16e37f25-e7a1-44e4-b899-63832c6194f1)

![ảnh](https://github.com/user-attachments/assets/36b61717-8b70-4b86-8584-9e74fb59dbf1)

Có tận 564 subdomain được tìm thấy.
Note: Để xác định được sub nào có thể truy cập thì chúng ta có thể sử dụng `httpx`.

![ảnh](https://github.com/user-attachments/assets/b9969a9a-8047-47af-80f4-1f37a1a33397)

# Discovering Sensitive Files

Để tìm kiếm các file hoặc directory nhạy cảm thì chúng ta có thể sử dụng `gobuster`, `ffuf`, `dirsearch`, `fexorbuster`.

![ảnh](https://github.com/user-attachments/assets/03f69996-4b33-4a4c-b50a-d85fcb84fdb4)

![ảnh](https://github.com/user-attachments/assets/ee14942e-212c-466e-b4f4-fb630abd1543)

# Google Hacking

Để tìm kiếm các site được public thì chúng ta có thể search `site:https://www.shopify.com/`

![ảnh](https://github.com/user-attachments/assets/937e7bd2-a2d0-4b9f-b03a-61e368b8759c)

Hầu như các site này không có gì đặc biệt. Tiếp đó chúng ta sẽ sử dụng filetype để tìm các file tài liệu chứa thông tin nhạy cảm bị bỏ quên.
`site:https://www.shopify.com filetype:pdf`

![ảnh](https://github.com/user-attachments/assets/0c8860f4-4d27-4654-8d24-b0b6e60247e4)

Các file pdf, docx, xls đều không được tìm thấy.












