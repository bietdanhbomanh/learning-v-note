Function là một khối lệnh làm một nhiệm vụ nhất định.
Như biến khi khai báo 1 function sẽ được lưu vào ram. khi nào execute/call function thì function mới thức thi. 

3 loại function:

-Cách khai báo
1.expression function:
variable = function nameFunction (parameter1, parameter2...){
    ...code...
    return value;
}
** nameFuncion là không bắt buộc. nó chỉ để mô tả hoặc note hàm cho rõ ràng

2. declaration function
function nameFunction (parameter1, parameter2...){
    ...code...
    return value;
}

3. arrow function (Cách viết ngắn gọn hơn 2 function trên)
(parameter1,parameter2...) => {
    ...code...
    return value;
}
* trả về luôn mà không có code 
(parameter1...) => value return; ** arrow function thích hợp để truyền vào một hàm khác (làm tham số của 1 hàm khác)

- cách gọi: khi gọi tham số (parameter) sẽ được gọi là đối số (argument).
1.expression function
variable(argument1, argument2...);
** Cách gọi lỗi:
nameFunction = (argument1, argument2...);
2.declaration function
nameFunction(argument1, argument2...);
3. arrow function
Ta có thể gán biến cho arrow function và gọi như expression function. như đã nói arrow funciton
cách ngắn gọn để làm một tham số cho 1 hàm khác nền thường không có tên.




