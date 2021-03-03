increment: ++
decrement: --

a++: sẽ trả về a rồi mới tăng lên 1
++a: tăng lên một rồi sau đó mới trả về a

ví dụ:
var a = 2;
++a + a++ - a--;

++a là bằng 3. Lúc này a sẽ trả về 3 luôn:
3 + a++ - a--;

a++: lúc này a vẫn là 3:
3 + 3 - a-- ; sau đó tăng lên 1. lúc này a = 4.

a--: a vẫn trả về 4:
==> 3 + 3 - 4. sau khi thực hiện thì a = 3.
