Khi dùng function làm tham số (function as a parameter) thì ta gọi đó là callback.

example:

function makingCoffee(done){
    console.log("Making coffee...");
    done();
}

makingCoffee(function(){
    console.log("done");
});
-> Ghi thẳng function vào

function makingCoffee(done){
    console.log("Making coffee...");
    done();
}

var done = function(){
    console.log("done");
}

makingCoffee(done);
->gán function cho biến, rồi dùng biến làm tham số





