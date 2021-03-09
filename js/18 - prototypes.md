Trong js function được coi là object và object cũng là một fuction cho nên function luôn có một object là prototype, trong prototype luôn chứa một constructor để khởi tạo nên object, và một vài property và methods được viếc sẵn bởi js hoặc được thêm vào bởi người code. 
constructor trong prototype chính là function đó:
Date.prototype.constructor === Date; -> true

mọi object được tạo từ constructor đó có thể truy cấp vào tất cả các thuộc tính và method của prototype của constructor đó.

ta có thể thêm các method và property vào constructor bằng cách:
Array.prototype.map2 = function () {
    codes
} -> với cách khai báo này (cách 2 là code thẳng vào constructor function) có thế tối ưu (best practice) được bộ nhớ. bởi vì khi dùng từ khóa new để tạo object, object sẽ khởi tạo sẽ không có thuột tính hay methods khởi tạo theo mà chỉ khi được gọi thì mới có.

và có thể dùng method map2 như method của Array:

[1, 2, 3 ].map2();

example:

function Mouse (color) {
    this.color = color;
    this.dead = false;
}

Mouse.prototype.die = function(){
    this.dead = true;
}

function Cat () {
    this.stomach = [];
}

Cat.prototype.eat = function(mouse) {
    this.stomach.push(mouse);
    mouse.die();
    return this;
}

var Mickey = new Mouse("Black");
var Jerry = new Mouse("Brown");

var tom = new Cat();
tom.eat(Mickey).eat(Jerry);

console.log(tom);

-> property stomach của object tom là mảng chứa 2 object Mouse có property dead = true.