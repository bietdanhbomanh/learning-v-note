1. setTimeout(callback, ms);
Dùng để chạy callback sau 1 khoảng ms
vì là một async method nên setTimeout sẽ chạy sau những hàm bình thường dù đặt là 0ms.

console.log('start');
setTimeout(function() {
    console.log('Mid');
},0);
console.log('end');

đoán xem kết quả :))

hàm sẽ trả về một id, được dùng cho hàm dưới

2. clearTimeout(id).
Để hủy bỏ medthod setTimeout

console.log('start');
var a = setTimeout(function() {
    console.log('Mid');
},0);
console.log('end');
clearTimeout(a);

3. setInterval(callback, ms). lặp callback sau một khoảng thời gian, trong setInterval ta có thể dùng clearTimeout(id) để dừng lặp.
example:

function count(a, b) {
    var c = setInterval(() => {
        console.log(a);
        a++
        if(a > b)
            clearTimeout(c);
    }, 1000);
}

count(5, 10)
->funciton đếm từ a đến b rồi dừng;

exampleAll:
function count(a, b) {
    if (a < b){
        return new Promise (function (resolve) {
            var c = setInterval(() => {
                console.log(a);
                a++
                if(a > b){
                    clearTimeout(c);
                    resolve();}
            }, 1000);
        })
    }
    else{
        return Promise.reject('oschos')
    }
}

function run(a, b) {
    count(a, b).then(function name(params) {
        console.log("Done");
    }).catch(function name(params) {
        console.log(params);
    })
}

->sau một khoảng thời gian đếm sẽ in ra done khi khoảng thành