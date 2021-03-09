Các module cài từ npm. SAU KHI CÀI MỚI SỬ DỤNG :

1.readline-sync: in ra một giá trị và nhận vào string
example: 
var readLineSync = require('readline-sync');
var input = readLineSync.question('Type some text');
console.log(input);

2.promise-fs
Giống như module fs trong nodejs tuy nhiên những phương thức sẽ không có truyền vào callback, thay vào đó sẽ trả về promise. khi đọc file thành công promise sẽ dùng then() callback của then sẽ trả về tham số của nội dung file. nếu không đọc đc file thì promise dùng catch() để báo lỗi.
var fs = require('promise-fs');

2. co
Học sau, khá giống promise.all