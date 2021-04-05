#### SQL injection UNION attacks 
Khi mà một ứng dụng lỗi SQL injection, kết quả gửi về trong responses của server thì UNiON attạck được gọi tên đầu tiên.
Để UNION query nó work thì phải có đủ hai điều kiện:
* Các individual queries phải trả về cùng một số cột
* Data type của mỗi cột phải compatible với các individual queries

_Điều này sẽ thường liên quan đến việc tìm ra:_
* Bao nhiêu cột được return từ truy vấn ban đầu
* Cột nào đc trả về chứa dữ liệu mà truy vấn ban đầu thực hiện
    
##### 1.Determining the number of columns required in an SQL injection UNION attack
OK, việc xác định này có hai cách: dùng ORDER BY và UNION SELECT. Chủ đề dùng US nên hong quan tâm OB cho lắm.

##### 2.Finding columns with a useful data type in an SQL injecton UNION attack

##### 3.Using SQL injection UNION attacks to retrieve interesting data

##### 4.Retrieving multiple values within a single column

