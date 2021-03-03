1.for.
- syntax: 
for (init; condition; final-expression) {
    codes
}
-example
for(var i = 1; i < 10; i++) {
    console.log(i);
}
=> Kết quả sẽ in ra 9 dòng lệnh in từ 1 đến 9

* biến khởi tạo trong vòng sẽ được thay đổi giá trị khi vòng lặp chạy
* condition(điều kiện) sai thì vòng lặp kết thúc
* final-expresstion phải giúp cho vòng lắp dẫn đến condition(điều kiện) sai nếu không vòng lặp
sẽ chạy mãi -> error

2.for ...of , for ...in
Lặp qua từng key hoặc value của object/array

-syntax:
for (var i of/in nameObject){
    codes
}
-example:
var array = ['Hello',13,'Kc'];
for (var i in array){
    console.log(i);

}
->kết quả sẽ in ra index của mảng từ 0 đến 2.
Nếu thay in là of. kết quả sẽ là value của từng index kết quả in ra từng dòng: Hello,13,Kc

=> biến khởi tạo i trong vòng lặp sẽ nhận được index/key của array/object nếu là for ...in.
nhận được value của array/object nếu là for...of.

3. while...do, do...white
a.while...do
-syntax:
while(condition){
    codes
}
-example:
var i = 1;
while(i <= 10 ){
    console.log('Hello');
    i++
}
->Kết quả in ra 10 dòng hello

Vòng lặp dừng khi condition (điều kiện) false. cho nên codes trong vòng lặp phải giúp condition phải dần tời condition false, nếu bỏ qua thì vòng lặp bị lặp mãi -> error
b.do...while
* so sánh với while ...do: while ...do dừng luôn vòng lặp nếu condition false, còn do...white sẽ lặp được ít nhất 1 lần nếu condition sai từ đầu.
-syntax:
do{
    codes
}white (condition);

-example:
var i = 1;
do {
    console.log('Hello');
    i++
}while(i == 10 );
->Kết quả sẽ in ra 1 dòng Hello, Điều kiện sai ngay từ đầu

Giống như while ...do. codes phải giúp dẫn đến condition false

5.Continue và break trong vòng lặp
if (contidion) continue;
->Bỏ qua "Lần lặp" hiện tại nếu condition true. Vòng lặp vẫn tiếp tục
if (contidion) break;
->Dừng vòng lặp nếu condition true. Thoát khỏi vòng lặp

