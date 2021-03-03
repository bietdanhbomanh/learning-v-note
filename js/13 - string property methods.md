var a = "github github";

* property:
1.length.
a.length -> 6

*methods
1.indexOf(): tìm index của chuỗi bất kỉ. trả về index đầu tiên tìm thấy
a.indexOf("th") -> 2, nếu tìm không thấy chuỗi thì trả về -1.
Ta có thể truyền tham số thứ 2 là indexStart, vị trí index tìm kiếm
a.indexOf("th", 3) -> 9

2.lastIndexOf(): tìm index của chuỗi bất kỉ từ phải qua trái. trả về index đầu tiên tìm thấy
a.lastIndexOf("th") -> 9

3.search().
Khá giống với indexOf(). không hỗ trợ tham số thứ 2, và có thể tìm biểu thức chính quy

4.slice(indexStart, indexEnd): cắt chuỗi
a.slice(3,6) -> hub
Khi bỏ tham số thứ 2:
a.slice(3) -> hub github

5.replace(find, replace):
a.replace("github", "js") -> js github
để replace tất cả ta dùng biểu thức chính quy (Học sau) cho tham số 1.
a.replace(/github/g, "js") -> js js

6.toUpperCase(), toLowerCase() : trả về chữ hoa và chữ thường

7.trim(): loại bỏ khoảng trắng 2 đầu
var b = "          github     "
b.trim() -> github

8.split("") :Chia string thành array bởi string tùy ý
a.split(" ") -> [github, github]
Nếu để trống thì string bị cắt thành từng 1 chữ:
a.split("") -> ["g", "i", "t", "h", "u", "b", " ", "g", "i", "t", "h", "u", "b"]

9.charAt(index): lấy kí tự ở index
a.charAt(2): -> t






