vì thực hiện đồng bộ (việc 1 xong trước việc 2, việc 2 cần dữ liệu trả về của việc 1 để chạy) ta dùng callback (sau khi công việc này thực hiện xong mới đến công việc khác) cho nên nhiều callback lồng nhau, dẫn tới rối rắm (callback hell hoặc pyramid of doom)

example:

setTimeout(function() {
    console.log(1);
    setTimeout(function() {
        console.log(1);
        setTimeout(function() {
            console.log(1);
            setTimeout(function() {
                console.log(1);
                setTimeout(function() {
                    console.log(1);
                    setTimeout(function() {
                        console.log(1);
                    }, 1000);
                }, 1000);
            }, 1000);
        }, 1000);
    }, 1000);
}, 1000);

-> console.log(1) để thể hiện một công việc khi việc ở ngoài chạy xong thì việc trong mới thực thi, nếu có nhiều callback -> callback hell.