Lập trình đồng bộ(sync) sẽ chạy code từ trên xuống dưới từ trái qua phải.

Lập trình bất đồng bộ(async), nhiều công việc có thể được thực hiện cùng lúc. Và nếu công việc thứ hai kết thúc trước, nó có thể sẽ cho ra kết quả trước cả câu lệnh thứ nhất. Vì thế, đôi khi kết quả của các câu lệnh sẽ không trả về đúng theo đúng thứ tự như trực quan của nó.

* ưu điểm và nhược điểm:
sync: chương trình sẽ chạy theo thứ tự từ trên xuống, nếu bị lỗi ở một câu lệnh cả chương trình sẽ dừng ->dễ kiểm soát và fix bug
-Nhược điểm: hiểu suất chậm, bởi vì một số câu lệnh phải chờ nhận dữ liệu ở bên ngoài thì câu lệnh tiếp theo mới chạy, thời gian chạy bẳng tổng thời gian tất cả các mã chạy.

async: sẽ giải quyết nhược điểm mà lập trình sync có là tất cả các công việc chạy cùng 1 lúc, công việc nào cần chờ thì chờ. còn công việc nào xong thì sẽ cho ra kết quả mà không cần đợi câu lệnh trước
-Nhược điểm: câu lệnh không thực hiện trên xuống do vậy khó kiểm soát, đòi hỏi kỹ thuật để kiểm soát


js là một ngôn ngữ đồng bộ chạy trên một luồng (thread), tuy nhiên có một số hàm + môi trường thực thi (browser, nodejs...) nên có thể chạy bất đồng bộ.

những kỉ thuật sử lý bất đồng bộ trong js: callback, promise, async await hoặc observable

->trong js hàm đồng bộ dù là tạc vụ nhẹ hay nặng sẽ luôn chạy trước(blocking) những hàm bất đồng bộ như promise, setTimeOut,setInterval... phải chạy sau cùng (none blocking)