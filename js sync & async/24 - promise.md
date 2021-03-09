promise giải quyết được vấn đề callback hell, nhưng không thay thế, chỉ khi gặp callback hell mới nên dùng promise, callback vẫn dễ hiểu hơn.

Promise là một function constructor. cho nên để tạo một promise. ta dùng keyword new, truyền vào đó một function.
syntax:

var promise = new Promise(
        <!-- executor function -->
    function(resolve, reject ) {
        logic codes
        resolve(data) -> Thành công
        reject (data) -> thất bại

    }
);

ngay khi gọi tới promise. function truyền trong đó sẽ thực thi ngay lập tức (executor) trước cả khi nhận được đối tượng vào biến.

function được truyền vào được trả về 2 tham số resolve, reject đều là 2 function, 2 function có thể truyền tham số vào là data.


Executor function để sử lí logic để gọi resolve() hoặc reject(), Chi một trong 2 được chạy.

Method để sử dụng đối tượng là một chuỗi phương thức (chaining method)
syntax:

promise.then(function).catch(function).finally(function);

then(). nhận đối số là một function, khi executor của promise gọi đến hàm resolve() thì then được chạy
catch(). nhận đối số là một function, khi executor của promise gọi đến hàm reject() thì catch được chạy
finally(). phương thức không bắt buộc trong promise, sẽ chạy khi 2 phương thức xử lý xong.

data được truyền vào resolve và reject sẽ được nhận ở tham số của callback ở phương thức then(function(dataOfResolve)) và catch(function(DataOfReject)).

example:
promise
    .then(function(x){
        console.log(x)
    })
    .catch(function(x){
        console.log(x)
    })
    .finally(function(){
        console.log("Done")
    });

promise sẽ có 3 trạng thái:
pendding: trạng thái treo -> leak memmory: xẩy ra khi executor funciton không gọi reject() hay resolve().
fulfilled: trạng thái thành công: khi gọi resolve() được gọi.
rejected: trạng thái thất bại: khi gọi reject() được gọi.

promise giải quyết vấn đề callback hell: tính chất chain (Chuỗi) của promise:

promise có thể gọi tới nhiều phương thức then() theo chuỗi

example:
promise 
    .then(function(x){
        console.log(x)
    })
    .then(function(x){
        console.log(x)
    })
    .then(function(x){
        console.log(x)
    })
    .catch(function(x){
        console.log(x)
    })

Một chuỗi then sẽ thực hiện đồng bộ. có nghĩa là method trước sẽ thực hiện rồi mới đến method then sau đó.

callback được truyền vào then() trước return ra gì thì sẽ làm đối số callback của then() kế tiếp:

promise 
    .then(function(){
        console.log(x)
        return data;
    })
    .then(function(data){
        console.log(data);
        return data2;
    })
    .then(function(data2){
        console.log(data2)
    })
    .catch(function(x){
        console.log(x)
    })

nếu callback của then() return về một giá trị (Không phải là promise) thì then() sau đó vẫn tiếp tục, cho dù giá trị return của then() trước đó chưa thực hiện xong

promise 
    .then(function(){
        console.log(x)
        return setTimeOut(function() {
            console.log(1)
        },1000)
    })
    .then(function(){
        console.log(2);
        return data2;
    })
    .catch(function(){
        console.log(x)
    })
-> kết quả sẽ in ra 2 trước 1.

nếu callback của then() trước return một object promise thì promise đó phải được thực hiện xong rồi mới tới then() tiếp theo, ví dụ sau:

promise
    .then(function() {
        return new Promise (
            function(resolve) {
                setTimeout(() => {
                    console.log(1);
                    resolve();
                }, 3000);
            }
        )
    })
    .then(function() {
        console.log(2);
    })
    .catch(functionx){
        console.log(x)
        
    })
    .finally(function(){
        console.log("Done")
    });

-> chờ 3000 xong in ra 1 rồi mới đến 2;   

nếu callback của then() trước return một promise, executor funciton của promise đó gọi resolve() hay reject() thì, then() hoặc catch() sau đó vẫn sẽ chạy tương ứng, data được truyền vào vẫn sẽ nhận được giống như cùng một đối tượng promise.

promise
    .then(function() {
        return new Promise(function(resolve, reject) {
            setTimeout(() => {
                console.log(1)
                reject("ok");
            }, 3000);
        })
    })
    .then(function() {
        console.log(2);
    })
    .catch(function(x){
        console.log(x);
        
    })


->bởi vì then() đầu tiên có callback gọi tới reject() và truyền vào "ok" nên catch() ở promise vẫn sẽ chạy và nhận đc "ok" -> codes sau 3s in ra 1 rồi sau đó in ra "ok" nhận từ Promise của return.

Ta có thể tạo nhanh một promise object mặc định là reject hay resolve và trả về value với syntax
promise.reject(value);
promise.resolve(value);

example:
var original = Promise.resolve(33);
var cast = Promise.resolve(original);
cast.then(function(value) {
  console.log('value: ' + value);
});
console.log('original === cast ? ' + (original === cast));

// original === cast ? true
// value: 33

-> ta có thể thấy orginal với cast là một.


Ta có cách để không chạy promise song song là viết một function rồi trả nó về một promise.

var a1 = new Promise(function(resolve) {
    setTimeout(() => {
        resolve([0]);
    }, 5000);
})

var a2 = function name(params) {
    return new Promise(function O(OK) {
        setTimeout(() => {
            OK([2, 3])
        }, 5000);
    })
}

var a, b;

a1
    .then(function name(params) {
        console.log(params);
        return a2();
    })
    .then(function name(params) {
        console.log(params)
    })
    .catch(function name(params) {
        
    });
    
;

-> để console.log trên in ra mảng chung. ta cần 10s.

Promise all sẽ cho phép chạy song song promise với nhau.

dùng promise all để chạy song song code trên ta chỉ mất 5s
Promise all chỉ trả về khi tất cả resolve xong. 
Nếu 1 trong promise bị reject thì sẽ không chạy, reject thì chạy phương thức ở catch(), sẽ nhận giá trị đầu tiên bị reject.
syntax:
Promise.all([promise1, promise2])
.then (function([valueOfpromise1, valueOfpromise2]) {

})
.catch (function(){

})

exampe:

var a1 = new Promise(function(resolve) {
    setTimeout(() => {
        resolve([0]);
    }, 5000);
})

var a2 = function name(params) {
    return new Promise(function O(OK) {
        setTimeout(() => {
            OK([2, 3])
        }, 5000);
    })
}

var all = Promise.all([a2(), a1]);

all
    .then((params) => {
            console.log(params[0].concat(params[1]));
    })
    .catch((params) => {
    })

-> mất 5s để nối mảng cả 2 giá trị, callback then() trả về value resolve tương ứng theo promise all đưa vào

