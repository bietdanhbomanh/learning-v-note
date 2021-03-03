Contructor là một funciton để khởi tạo(xây dựng) một object bằng từ khóa new.
Tên contructor thường được việt hoa chữ đầu khác với kiểu đặt biến là (camelCase)
example:

function Mouse(name, color) {
    this.name = name;
    this.color = color;

}
var mouse1 = new Mouse("M1","Trắng");
var mouse2 = new Mouse("M2","Nâu");
var mouse3 = new Mouse("M3","Vàng");


var tom = {
    name: "tom",
    stomach: [],
    eat: function(mouse) {
        this.stomach.push(mouse);
        return this;
    }
}

tom.eat(mouse1).eat(mouse2).eat(mouse3);  /*Nhờ method eat của object tom return this có nghĩa là return
chính nó nên ta có thể sử dụng method chaining như trên */

console.log(tom);


=>Constructor tiện lợi khi tạo các object có các thuột tính và phương thức tương tự một cách ngắn gọn.
