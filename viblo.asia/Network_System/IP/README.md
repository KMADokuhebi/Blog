###### Đây là blog nơi ghi lại kiến thức học được qua từng ngày
## Subnet, Subnetmask, chia subnet Subneting ?
__Thoi để lấy cái ví dụ nhẹ cái__
> 1 subnet có ip `128.42.5.4` cho subnet mask `255.255.248.0` (510 ip address)
>
> hay `128.42.5.4/21` (510 ip address)

_Nếu thấy vấn đề vì sao được 510 ip vậy thì đọc tiếp hong thì thoi nhé_
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
Đến tất cả bit *1* của _Subnetmask_ thì ta có số _Prefix_=21 . Vậy 21 bit đầu là đánh địa chỉ cho network, còn lại `32-21=9` là số Host 
để đánh cho mạng đó
### Subneting- chia mạng con 
Thêm tí ví dụ nữa là sử dụng `128.42.0.0` đẻ chia thành 3 mạng con nữa để cho 3 phòng sửa dụng.
Để chia thêm 3 thì phải mượn 2 bit để đánh cho 4 các host trong network (vì sao mượn 2 mà không phải là 1 thì đọc hết ròi ngẫm lại là ok)
| Địa chỉ subnet| Binary                                 | Decimal       | Các Host ip               |  
| :-----------: |:--------------------------------:      |:-------------:|:------------------------: | 
| Subnet 1      |10000000 00101010 00000**00**0 00000000 | 128.42.0.0    | 128.42.0.1 ~ 128.42.1.254 |            
| Subnet 2      |10000000 00101010 00000**01**0 00000000 | 128.42.2.0    | 128.42.2.1 ~ 128.42.3.254 | 
| Subnet 3      |10000000 00101010 00000**10**0 00000000 | 128.42.4.0    | 128.42.4.1 ~ 128.42.5.254 |  
| Subnet 4      |10000000 00101010 00000**11**0 00000000 | 128.42.6.0    | 128.42.6.1 ~ 128.42.7.254 | 

4 Subnet trên dùng _23_ bit đầu để đánh địa chỉ cho chính mạng đó. Hãy để ý bit thứ _22_ và _23_ đó là hai bit mượn, có 4 trường hợn tất cả 00,01,10,11 
cho 4 Subnet tương ứng. Đọc tới đây thì các bạn hiểu vì sao cần chia ba lại mượn 2 bit Host rồi đấy.
### Tính số lượng các các host tối đa mà ta có thể đánh địa chỉ IP trong mỗi subnet
OK nào vì Subnet trên đã dùng _23_ địa chỉ đầu để đánh địa chỉ mạng ròi nên `32=23=9` địa chỉ sau sẽ được đánh IP cho Host trong mạng.
Số ip đựa chia sẽ là `2^9 -2 =510`.Lấy Subnet 1 làm vd *Trừ 2* là vì ta dùng `128.42.0.0`làm địa chỉ Subnet và `128.42.1.255` làm địa chỉ Broadcast
(Broadcast là địa chỉ có phần host là *1*: `128.42.1.255` ->> `10000000 00101010 00000001 11111111`)
#### Bạn đã hiểu vấn đề chưa? nếu chưa hiểu thì đọc lại từ đầu nhé.


