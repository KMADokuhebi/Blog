###### Đây là blog nơi ghi lại kiến thức học được qua từng ngày
## Subnet, Subnetmask, chia subnet Subneting ?
__Thoi để lấy cái ví dụ nhẹ cái__
> 1 subnet có ip `128.42.5.4` cho subnet mask `255.255.248.0` (510 ip address)
>
> hay `128.42.5.4/21` (510 ip address)

_Nếu thấy vấn đề vì sao vậy thì đọc tiếp hong thì thoi nhé_
### Một chút về IP
Ip gồm **32** bit :(theo ví dụ sẽ là) `10000000 00101010 00000101 00000100` mỗi dãi là 8 bit gọi là **octet**
 
Ip sẽ được cấu tạo gồm 2 phần `[Network][Host]`
* `[Network]` xác định network đó
* `[Host]` để đánh cho các thiết bị trong mạng network đó
Nếu ta muốn gửi một gói tin đến địa chỉ `128.42.5.4` thì k thể biết đc phần `Network` ip ở đâu nên phải thêm _Subnetmask_ 

Theo ví dụ thì _Subnetmask_ `255.255.248.0` đổi ra hệ nhị phân sẽ là `11111111 11111111 11111000 00000000`
Thực hiện phép AND 
```
Ip        :  128.42.5.4     binayry  10000000 00101010 00000101 00000100
Subnetmask:  255.255.248.0  binayry  11111111 11111111 11111000 00000000
                                                            |  AND có sự thay đổi ở bit thứ 21 trở đi
                                     10000000 00101010 00000 --> 128.42.0.0                      
```

 
 

