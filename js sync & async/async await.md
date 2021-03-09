Xuất hiện trong phiên bản js mới >= 7.6
Gọi là async fuction, trong funciton nay có toán tử await, để await promise và return value resovle.
async function này sẽ trả về một promise.
Các lệnh trong trong promise chỉ thực thi khi tất cả các promise đều resolve, và thực hiện theo thứ tự kể cả bất đồng bộ hay đồng bộ.
example:
