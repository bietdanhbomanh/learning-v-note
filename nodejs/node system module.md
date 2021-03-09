node js là một môi trường thưc thi js. tương tự với trình duyệt.
trong node js có hệ thống module mà trình duyệt không có.

module có thể tách các constructor function thành nhiều file nhỏ, đề rõ ràng và dễ quản lý; ta có thể tách bất cứ thành phần nào thành module.

từ file chính ta có thể nhúng các file module đề sử dụng.

syntax:
-module file:
module.export = value, với value là gì tùy ý (Ta nên dùng để tách constructor function);
nên để dòng code này ở cuối file

-main file:
require('path/fileName.js');
Module file export ra gì thì hàm require ở file main require được giá trị đó. nên sử dụng ở đầu file 

example.

file1: cat.js

function Cat () {
    this.stomach = [];
}
Cat.prototype.eat = function(mouse) {
    this.stomach.push(mouse);
    mouse.die();
    return this;
}

module.exports = Cat;

file2: mouse.js

function Mouse (color) {
    this.color = color;
    this.dead = false;
}
Mouse.prototype.die = function(){
    this.dead = true;
}
module.exports = Mouse;

file 3: catEatMouse.js

var Cat = require('./cat')
var Mouse = require('./mouse');
var Mickey = new Mouse("Black");
var Jerry = new Mouse("Brown");
var tom = new Cat();
tom.eat(Mickey).eat(Jerry);
console.log(tom);

-> với 3 file trên trong 1 folder và thực thi với node js với lệnh 'node catEatMouse', nếu chạy ở trình duyệt sẽ bị lỗi

Built-in modlue: những module đc dựng sẵn trong nodejs.

1.File system.
Đọc và ghi file. là một module object dựng sẵn. có những phương thức để sử dụng.

example:
var fs = require('fs');

ta thường đặt biến cùng với tên module require, với require module hệ thống, đường dẫn là không cần thiết như module tự định nghĩa

Method: readFileSync

fs.readFileSync(pathFile, option)

Với option là object hoặc string, chứa trong ecoding (bộ giải mã);

example

var a = fs.readFileSync('./index.htm', {encoding:'utf8'});
console.log(a);

Method: writeFileSync

fs.reFileSync(pathFile,data, option)

Với option là object hoặc string, chứa 1 trong ecoding (bộ giải mã), ecoding trong mặc định fs.writeFileSync là 'utf8' ta không cần khai báo

example:

fs.writeFileSync('./index2.htm',a);

Nếu chưa có file thì sẽ tạo ra, nếu có sẵn thì bị ghi đè.

Method: readFile.(Đọc file không đồng bộ async);
fs.readFile(pathFile, option, callback(err, data));
callback sẽ đc thực hiện khi chạy xong
callback trên sẽ nhận 2 tham số err, data.
data khi readfile thành công, data sẽ nhận nội dung file.
err khi readfile lỗi.

