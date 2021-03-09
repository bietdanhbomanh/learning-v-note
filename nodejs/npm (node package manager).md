ngoài module có sẵn trong node(built-in), module ta tự code thì để xây dựng một app ta cần thêm nhiều module khác tự cộng đồng dựng lên

Khi cài node ta có nodejs là môi trường và công cụ npm. ta dùng npm để cài những module vào hệ thống nodejs.
xem và cài các module ngoài tại mpnjs.com.

để khởi động một project có sử dụng npm ta dùng lệnh:
npm init
sau đó hệ thống hỏi một số câu hỏi để khởi tạo thông tin project đc lưu vào file json.
sau đó cài module bằng lệnh:
npm install nameModule --save. hậu tố --save để lưu thông tin vào file json. lệnh này chỉ cài module vào file project. ta có lệnh khác để cài module vào nodejs.

example: 
npm install readline-sync --save
sau khi cài xong thì file json mô tả thêm.
"dependencies": {
    "readline-sync": "^1.4.10"
}

có nghĩa là project đang phụ thuộc vào những module có trong key "dependencies", cần có những module đó để project có thể hoạt động bình thường.

cách dùng module như là system module.
var readLineSync = require('readline-sync');

Module readline-sync có phương thức question() in ra một value và return string nhập vào.

var a = readLineSync.question('Tên bạn là: ');

dòng code console.log ra chuỗi và nhận lại giá trị nhập r gán vào a;