0.forEach(): nhận tham số là một callback,call back có 2 tham số element và index.
example:
var rectangles = [
    {w: 10, h: 5},
    {w: 3, h: 4},
    {w: 1, h: 5},
];

rectangles.forEach(function(element,index) {
    console.log(index+':',element);
})
->in ra index và value của mảng

1.every(): duyệt qua từng phần tử của mảng và kiểm tra điều kiện. trả về true nếu tất cả phần tử thỏa mãn điều kiện, false nếu sai.
Nếu một phần tử sai thì sẽ ngừng duyệt và trả về false.

var rectangles = [
    {w: 10, h: 5},
    {w: 3, h: 4},
    {w: 1, h: 5},
];

var h5 = rectangles.every(function(element, index) {
    console.log(element);
    return element.h == 5;
})

console.log(h5)
->codes trên chỉ in ra được 2 phần tử. vì phần tử thứ 2 không thõa mãn điều kiện nên element không thể duyệt đến phần tử tiếp theo. và trả về h5 là false

2.some():Giống với every() và ngược lại. duyệt qua và kiểm trả phần tử. nếu một phần tử trả về true thì sẽ dừng duyệt ở phần tử đó và trả về true. 

3.find(): duyệt qua phần tử. trả về phần tử đầu tiên thỏa mãn điều kiện và dừng duyệt. trả về undifined nếu Không có gì thõa mãn
var rectangles = [
    {w: 10, h: 5},
    {w: 3, h: 4},
    {w: 1, h: 5},
];

var w3 = rectangles.find(function(element, index) {
    return element.w == 3;
});

console.log(w3);
-> in ra phần tử {w: 3, h: 4}.

4.filter():Duyệt qua tất cả phần tử, trả về mảng tất cả phần tử thõa mãn

var rectangles = [
    {w: 10, h: 5},
    {w: 3, h: 4},
    {w: 3, h: 4},
    {w: 1, h: 5},
];

var w3 = rectangles.find(function(element, index) {
    return element.w == 3;
});

console.log(w3);
-> in ra mảng có 2 phần tử [{w: 3, h: 4}, {w: 3, h: 4}]

5.map(element, index): nhận tham số là một callback, tham số của callback sẽ duyệt qua từng phần tử mảng. trả về mảng mới
-example: 
var rectangles = [
    {w: 10, h: 5},
    {w: 3, h: 4},
    {w: 1, h: 5},
];

var s = rectangles.map(function(element) {
    return element.w * element.h;
})
-> ta có mảng s là diện tích của hình chủ nhật biến đổi từ mảng rectangles.

-example2:
var courses = [
    {id: 1,
    name: "js"},
    {id: 2,
    name: "ruby"},
    {id: 3,
    name: "php"}
]

var newCourses = courses.map(function(course){
    course.coin = 0;
    course.name = "Khóa học "+course.name;
    return course;

}) 

console.log(newCourses);

->in ra mảng mà các phần tử thay đổi. thêm key coin và sửa name vào object của mỗi phần tử.


6.reduce(): lấy và xử lý từng phần tử để cho ra một kết quả. nhận 2 tham số callback và initalValue, callback tham số bắt buộc và initialValue là khởi tạo giá trị ban đầu có thể là mảng, string .... callback nhận 4 tham số accumulator: biến lưu trữ, element: element đang duyệt , Index: chỉ mục hiện tại đang duyệt và originArray: mảng gốc gọi tới reduce().

example:
var rectangles = [
    {w: 10, h: 5},
    {w: 3, h: 4},
    {w: 1, h: 5},
];

var totalW = rectangles.reduce(function(accumulator, element) {
    return accumulator + element.w;
}, 0)

console.log(totalW);
-> in ra tổng giá trị của w từ những phần tử.

example2:
var orders = [
    {
        name: "A",
        quantity: 2,
        unitPrice: 200
    },

    {
        name: "B",
        quantity: 6,
        unitPrice: 100
    },

    {
        name: "C",
        quantity: 7,
        unitPrice: 300
    },
]

var totalOrders = orders.reduce(function(accumulator, element) {
    return accumulator + element.quantity * element.unitPrice;
}, 0)

console.log(totalOrders);
-> in ra tổng giá tất cả sản phẩm

* Nếu không cho vào tham số initialValue thì lần lặp đầu tiên tham số accumulator của callback sẽ là phần tử đầu tiên của mảng, element sẽ là phần tử số 2. callback return sẽ được lưu vào accumulator cho lần lặp tiếp theo

7.soft(): Sắp xếp mảng trả về mảng đã sắp xếp. tham số là callback với 2 tham số nhận 2 phần tử bất kì.
Cách hoạt động. callback sẽ return về một giá trị:
nếu giá trị return nhỏ hơn 0 thì phần từ thứ nhất sẽ xếp trước.
nếu giá trị return lớn hơn 0 thì phần từ thứ hai sẽ xếp trước.
nếu giá trị return bằng 0 thì phần từ không đổi.


example:
var array = [7, 4, 8, 1, 2, ]
array.soft(function(a, b) {
    return a - b.
})
-> Sắp xếp số từ nhỏ đến lớn (ascending number);

example2:
var employees = [
    {
        name: "Tí",
        age: 25
    },
    {
        name: "Mara",
        age: 30
    },
    {
        name: "Thảo",
        age: 19
    }
]
var descendingAge = employees.sort(function(a, b) {
    return b.age - a.age;
})

console.log(descendingAge)
-> sắp xếp object trong mảng theo key age. từ lớn đến nhỏ (descending number)




