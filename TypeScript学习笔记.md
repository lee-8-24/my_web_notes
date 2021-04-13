# TypeScript学习笔记

## 一、Typescript是什么

类型脚本，所以类型是很重要的，TypeScript是JavaScript类型的超集，可以编译成纯JavaScript。

但是需要给JS加上可选的类型系统，加上静态类型后，能将调试从运行期提前到编码期

## 二、配置



### 1、let和const

已经不再使用JS中的Varley，加上类型说明：

```typescript
let test_1:string='Hello TypeScript!';
console.log(test_1);
```

联合类型

```typescript
let test_2:string | number='TS';
```



### 2、解构

可以把对象和数组的元素拆分到指定变量中，方便使用

```typescript
let test_3=[1,2,3,4];
let [fir,se]=test_3;
console.log(fir);
console.log(se);
let [one,...other]=test_3;
console.log(other);
let newArr=[89,...test_3,18];
console.log(newArr);
```

`...other`表示将剩余的数组展开



### 3、函数

```typescript
// 定义函数
function greeting(firstName:string,lastName:string):string{
    return 'Hello'+' '+firstName+lastName;
}
console.log(greeting('Lee ','zhuo '));
```

定义函数需要注意的点：

`变量名:类型`

`function 函数名():返回值类型{}`



### 4、可选参数

`变量名?:类型`  表示的意思是，如果有这个变量，则变量类型为指定类型，如果没有就算了

```typescript
// 可选参数的函数
function greeting(firstName:string,lastName?:string):string{
    if(lastName)
        return 'Hello'+' '+firstName+lastName;
    else
        return 'Hello'+' '+firstName;
}
console.log(greeting('Lee ','Zhuo '));

```



### 5、默认参数

==当有默认参数时，如果不输则默认为默认参数，如果有传递实参则给出实参的值==

```typescript
// 默认参数
function greeting(firstName:string,lastName='ZZ'):string{
    return 'Hello'+' '+firstName+lastName;
}
console.log(greeting('Lee '));
```



### 6、剩余参数

必要参数，默认参数和可选参数有个共同点：它们表示某一个参数。 有时，你想同时操作多个参数，或者你并不知道会有多少参数传递进来， 在TypeScript里，你可以把所有参数收集到一个变量里

```typescript
//剩余参数，会被当做个数不限的可选参数。可以一个都没有，也可以有任意个
function greeting(firstName: string, ...restName: string[]) {
  return `Hello ${firstName} ${restName.join(' ')}!`;
}
console.log(greeting('Osama', 'bin', 'Muhammad', 'bin', 'Awad', 'bin', 'Laden'));
console.log(greeting('Laden'));
```



### 7、箭头函数

```typescript
//无参数，函数体代码只有一行，则该行结果即为函数返回值
let greeting1 = () => `Hello TS!`;
console.log(greeting1());
//一个参数，函数体代码只有一行，则该行结果即为函数返回值
let greeting2 = (name: string) => `Hello ${name}`;
console.log(greeting2('QiGe'));
//两个及以上的参数，函数体代码只有一行，则该行结果即为函数返回值
let add1 = (n1: number, n2: number) => n1 + n2;
console.log(add1(1, 2));
//两个及以上的参数，函数体代码多于一行,则必须用{}包裹，且显式给出return
let add2 = (n1: number, n2: number) => {
  let sum = n1 + n2;
  return sum;//改为sum++结果如何？
}
console.log(add2(1, 2));
```



### 8、关于类

类是生成对象过着类实例的模板，Angular宽假大量使用类

```typescript
class CAR{
    name: string;
    place:string;
    constructor(name:string,place:string){
        this.name=name;
        this.place=place;
    }
    show():void{
        console.log(this.name);
        console.log(this.place);
    }
}
let mycar=new CAR("baoma","chongqing");
mycar.show();
```

这里的类和C++的类基本上一致，用法也类似

当然类也是有访问权限的，当然和C++一样，私有属性只能内部访问，共有属性才能外部访问。

例如，将name定义为private的话，在外调用则会报错。

**存取器-getter、setter**

设置getter和setter操作其private属性，即使public属性也是这样

```typescript

//getter和setter
class MyInfo { //class是关键字，类名默认全部大写首字母
  private readonly _name: string; //私有属性，外部不可访问。readonly使其只能在初始化时赋值，以后不可更改。    
  private _weather: string; //私有属性，习惯以_开头进行命名

  constructor(name: string, weather: string){ //构造函数，一般用于初始化
    this._name = name;
    this._weather = weather;
  }
  get name(): string {
    return this._name;
  }
  set name(value: string) {  //error！ _name有readonly属性
    this._name = value;
  }
  get weather(): string {
    return this._weather;
  }
  set weather(value: string) {
    this._weather = value;
  } 
}
  
let myData = new MyInfo('QiGe', 'raining'); //使用new关键字生成对象
console.log(myData.name, myData.weather);
myData.weather = 'sunny'; //OK
myData.name = 'Wang'; //error!
console.log(myData);
          
```

### 9、静态属性

类中的属性或函数有static修饰，则可直接使用而不需要实例化

```typescript

//静态属性，内建或自定义，无需new即可使用
console.log(Math.round(89.64)); //90
console.log(Math.pow(2, 8)); //256
class MyStaticClass {
  static place = 'Earth';
  static printInfo() {
    console.log('We have only one Earth!');
  }
}
console.log(MyStaticClass.place);
MyStaticClass.printInfo();
          
```



### 10、继承

可以通过`extends`关键字继承其它类，从而成为其子类

```typescript

class Animal {
  // 当构造函数传入的参数加上了“访问权限控制符”，则同时会声明同名类属性，并赋值
  constructor(public name: string) { }
  protected log(message: string) {
    console.log(message);
  }
  move(distanceInMeters: number = 0) {        
    this.log(`${this.name} moved ${distanceInMeters}m.`);//请注意name来自何处
    this.log('==============');
  }
}

class Horse extends Animal {
  constructor(name: string) { 
    super(name); // 通过super调用父类构造器
  }
  run(distanceInMeters = 50) { //自己独有的函数
    this.log("Clop, clop..."); 
    super.move(distanceInMeters); // 通过super调用父类方法
  }
}

class Eagle extends Animal {
  constructor(name: string) { super(name); }
  reborn() { //自己独有的函数
    console.log('Reborn？ It is a joke, hahaha!');
  }

}

let tom: Horse = new Horse("Tommy the Palomino");
tom.run(8964);
let sam: Eagle = new Eagle("Sammy the Hawk");
sam.move(1024);//sam的move函数来自何处？
sam.reborn();
          
```



### 11、模块

对于大型的项目，我们需要使用模块进行管理。每个 .ts 文件就是一个模块，通过 export 来对外部模块暴露元素，通过 import 来引入模块。

在项目文件夹下新建目录modules和文件main.ts，并在modules下新建name.ts和weather.ts文件，如下：

```typescript
//用import从外部模块文件导入，默认后缀.ts去掉
import { Name } from "./modules/name";
import { WeatherLocation } from "./modules/weather";

let name = new Name('Wang', 'Yong');
let loc = new WeatherLocation('raining', 'ChongQing');

console.log(name.nameMessage);
console.log(loc.weatherMessage);    
```

