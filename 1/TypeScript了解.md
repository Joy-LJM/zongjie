### 更强的类型检查：函数形参定义类型，实参不符合就报错
function showAge(age:number){
    return age;
}
console.log(showAge('12')); // 报错

### TS显式定义：变量定义时加类型定义
let username:string = "big bin brother";
let age:number = 12;
let isHandsome:boolean = true;
let girlFriend:object = {
    "name":"如花",
    "age":18
};
let arrStudent = ["狗剩","二蛋","三娃","百万","富贵"];

### 强类型 => 只能同类型添加
let arrStudent = ["狗剩","二蛋","三娃","百万","富贵"];
arrStudent.push(12); // 报错
### any类型，
- 数据随便装，很不推荐使用。
let arrAges:any[] = [12,5,8,'99'];