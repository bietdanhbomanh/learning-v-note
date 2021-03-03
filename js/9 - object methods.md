khi một function được khai báo trong một object thì đc gọi là method.

person = {
    name:"Name",
    lastName:"Last Name",
    getFullName: function() {
        return this.name + " " + this.lastName
    }

}

Gọi method của một đối tượng:
person.getFullName();  

Kết quá trả về là "Name Last Name";

**Từ khóa this được khai báo trong method trên là object gọi tới method (this ở trương hợp trên là object person) .


