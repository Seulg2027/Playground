## Typescript ๐

1. ํ์์คํฌ๋ฆฝํธ๋ฅผ ์ฌ์ฉํ๋ ์ด์ ?  
: typescript -> javascript๋ก ์ ํํด์ ์ฌ์ฉ  
: ๊ทธ๋ฐ๋ฐ ์ ์ฌ์ฉํ๋๊ฑธ๊น?
```javascript
function add(num1, num2){
    console.log(num1+num2);
}

add();
add(1);
add(1,2);
// ํ๋ผ๋ฏธํฐ๊ฐ ๋ ๊ฐ์ฌ์ผํ๋ ํจ์์ธ๋ฐ ๋ชจ๋ ์๋ฌ์์ด ์ถ๋ ฅ

function showItems(arr){
    arr.forEach((item)=>{
        console.log(item);
    });
}
showItems([1, 2, 3]); //์ ๋๋ก ์ถ๋ ฅ
showItems(1, 2, 3); // ์ค๋ฅ๊ฐ ๋๋ฉด์ ์คํ X
```
* javascript๋ ๋์ ์ธ์ด์ด๊ณ , **๋ฐํ์**์ ํ์ ๊ฒฐ์ ํ๊ณ  ์ค๋ฅ๋ฅผ ๋ฐ๊ฒฌํ๋ค.
* typescript๋ ์ ์ ์ธ์ด. **์ปจํ์ผ ํ์**์ ํ์ ๊ฒฐ์ ํ๊ณ  ์ค๋ฅ๋ฅผ ๋ฐ๊ฒฌํ๋ค.  
=> ๋ฐ๋ผ์ ํ์์คํฌ๋ฆฝํธ๋ ์คํ์ํค์ง ์์๋ ์๋ฌ๋ฅผ ๋ฐ๊ฒฌํ๊ธฐ ์ฝ๋ค.   
์ ์ฝ๋๋ฅผ ํ์์คํฌ๋ฆฝํธ๋ก ์์ฑํ ์ฝ๋๋ ๋ค์๊ณผ ๊ฐ๋ค.
```typescript
function add(num1:number, num2:number){
    console.log(num1+num2);
}

add(1, 2);
```
    
2. ๊ธฐ๋ณธํ์

```typescript
let age:number = 30;
let isAdult:boolean = true;
let a:number[] = [1,2,3];
let a2:Array<number> = [1,2,3];

let week:string[] = ['mon', 'tue', 'wed'];
let week2:Array<string> = ['mon', 'tue', 'wed'];
// a, a2 ์ week, week2 ๋ชจ๋ ๊ฐ์ ๋ฐฐ์ด ํ ๋น
```

ํํ(Tuple)
void๋ ์๋ฌด ๊ฒ๋ ๋ฐํํ์ง ์์ ๋ ์ฌ์ฉํ๋ค.  
never๋ ํญ์ ์๋ฌ๋ฅผ ๋ฐํํ๊ฑฐ๋, ์์ํ ๋๋์ง ์๋ ํ์์ ํจ์๋ก ์ฌ์ฉ์ด ๊ฐ๋ฅํ๋ค. 
```typescript
let b:[string, number];

b = ['z',1];

b[0].toLowerCase();

//void, never
function sayHello():void{
    console.log('hello');
}

function showError():never{
    throw new Error();
}

function infLoop():never{
    while(true){
        //
    }
}
``` 

enum์ javascript์์๋ ์ฌ์ฉํ์ง ์๋ ํ์์ด๋ค. ๋น์ทํ ํ์๋ผ๋ฆฌ ๋ฌถ์ด์ค ๊ฒ์ด๋ค.

```typescript
enum Os{
    Window = 3,
    Ios = 10,
    Android
}

console.log(Os['Ios']);

let myOs:Os;
// ํ์์ ์ด๋ ๊ฒ ์ค์ ํด์ฃผ๋ฉด Win, Ios, And ๋ง ์๋ ฅํ  ์ ์์
myOs = Os.Window
// ํน์ ๊ฐ๋ง ์๋ ฅํ  ์ ์๊ณ  ๊ทธ ๊ฐ๋ค์ด ๊ณตํต์ ์ด ์์ ๋ enum์ ์ฌ์ฉํ๋ฉด ์ข์

//null, undefined
let a:null = null;
let b:undefined = undefined;
```

3. ์ธํฐํ์ด์ค(Interface)  
์ธํฐํ์ด์ค๋ฅผ ์ฌ์ฉํ๋ฉด ์ด๋ ํ ๊ฐ์ฒด๊ฐ ๋ฌด์จ ํ๋กํผํฐ๋ ๋ฉ์๋๋ฅผ ๊ฐ์ก๋์ง ์ ์ ์๋ค.
```typescript
let user:object;
user = {
    name :'xx',
    age : 30
}
console.log(user.name) // ์๋ฌ๊ฐ ๋ฌ๋ค.
// ์ด๋ด ๋ ์ฌ์ฉํด ์ฃผ๋ ๊ฒ์ด ์ธํฐํ์ด์ค~~~

type Score = 'A' | 'B' | 'C' | 'F';

interface User {
    name : string;
    age : number;
    gender? : string; //์๋ ฅํด๋ ๋๊ณ , ์ํด๋ ๋๋ ์์ฑ์ ํ์ํ  ๋ ?๋ฅผ ์น๋ค.
    readonly birthYear : number; //์ฝ๊ธฐ์ ์ฉ์ธ ์์ฑ
    [grade:number] : Score; // enumํ์์ผ๋ก ํ์ ์ค์ 
}

let user : User = {
    name : 'xx',
    age : 30
    birthYear : 2000,
    1 : 'A',
    2 : 'B'
}
user.age = 10;
user.gender = 'male';
```
์ธํฐํ์ด์ค ํจ์๋ฅผ ๋ง๋ค์ด๋ณด์.
```typescript
// 1๋ฒ
interface Add {
    (num1:number, num2:number): number; // ๋ํ ์ซ์๋ฅผ ๋ฆฌํดํด์ค๋ค.
}
const add : Add = function(x, y){
    return x + y;
}

add(10, 20); //30

// 2๋ฒ
interface IsAdult {
    (age:number) : boolean;
}
const a:IsAdult = (age) =>{
    return age > 19;
}

a(33); //True

//Implements
interface Car {
    color: string;
    wheels: number;
    start(): void;
}

interface Benz extends Car{ //Car ์ธํฐํ์ด์ค์์ ํ์ฅํด์ค๋ค.
    door: number;
    stop(): void;
}
```