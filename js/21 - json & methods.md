json là một định dạng dữ liệu, đơn giản chỉ là một string.

json = JavaScript Object Notation.
json được phát kiến với js.

Json thể hiện được các kiểu dữ liệu: Array, object, boolean, null, number, string

* syntax:
json là một string cho nên js ta cho vô đấu '' ;
thể hiện string trong json ta cho vô đấu "";
thể hiện mảng  [];
thể hiện object {};
thể hiện số, null, boolean không cần dấu
ngăn cách phần tử bởi dấu "," ;
không được thừa dấu "," ở phần tử cuối

example:
var json = '[ {"name": "Pham Tai", "age": 18, "girlfriend": false}, 
{"name": "Pham Tai", "age": 18, "girlfriend": false}]'

-> json trên thể hiện mảng có 2 đối tượng giống nhau.

* Phương thức làm việc với json trong js.

stringnify(json); -> convert from datatypes to json.
parse(datatypes); -> convert from json to datapytes.

