var array1 = ['js','php','java'];
var array2 = ['html','css'];

1.toString(): Chuyển mảng về string, cách bởi dấu phẩy
array1.toString(); -> js,php,java

2.join(): Chuyển mảng về string, cách bởi tùy ý (đối số của join)
array1.join("1")   -> js1php1java
array1.join("")   -> jsphpjava

3.pop(): xóa phần tử cuối và trả về.
array1.pop() -> java.

4.push(): thêm phần tử vào cuối mảng trả về số phần tử mảng.
array1.push('html','css') -> 5

5.shift(): xóa phần từ đầu và trả về
array1.shift() -> js

6.unshift(): thêm phần tử vào ĐẦU mảng trả về số phần tử mảng.
array1.push('html','css') -> 5

7.splice(indexStart, deletelCount, add... ): Xóa, thêm linh hoạt trong mảng
array1.splice(1, 1) : Tại index 1, xóa đi 1 phân tử và trả về phần tử đã xóa
array1.splice(1, 0, 'css', 'html') : Tại index 1, chèn phần tử và trả về mảng rỗng

8.concat(array): Nối mảng vào một mảng
array1.concat(array2): -> array1 = ['js','php','java','html','css']

9.slice(startIndex, endIndex): cắt và trả về mảng cắt
tham số endIndex không bắt buộc, không có than số endIndex thì cắt hết