# Рефакторинг кода 
___________________________________________________
## Лабораторная работа 7

В данной лабораторной работе рефакторить код написанный на javascript

### Задание 1. level stone

Скрипт сравнивает две переменные и выводит равны они или нет

```js
let a = prompt('var one'); 
let c = prompt('var two');
if (a == c) 
console.log('equally')
else 
console.log('not equally');
let b = 'world'; 
a = a + b;
console.log(a);
```

### Задание №2. level iron

Скрипт выводит названия фруктов, а затем отображает название фрукта и его цвет

```js
let f = new Array('apple', 'strawberry', 'blueberry', 'raspberry', 'lemon');
console.log(f);

for (let i =0; i<f.length; i++)
{
    if (f[i] === 'apple') console.log('apple green')
    if (f[i] === 'strawberry') console.log('strawberry red')
    if (f[i] === 'blueberry') console.log('blueberry blue')
    if (f[i] === 'raspberry') console.log('raspberry light red')
    if (f[i] === 'lemon') console.log('lemon yellow')
}
```

### Задание 3. level gold

Скрипт выполняет подсчет затрат на зарплату сотрудникам.  
Где спрашивает у пользователя кол-во сотрудников и зарплату на одного человека

```js
let d=prompt('Введите кол-во человек ');
if (!isNaN(parseFloat(d)))
{
    d=parseFloat(d)
}
else
{
    d = 0;
}

let k=prompt('Введите зарплату на человека ');
if (!isNaN(parseFloat(k)))
{
    k=parseFloat(k);
} 
else 
{
    k=0;
}

alert('Затраты на ЗП: ' + d*k);
```
### Задание 4

Скрипт проводит анализ имеющихся студентов в массиве.
Выводит среднюю оценку и список плохих студентов

```js

let Students = [
    {FIO:'Петров А.А.',mark:5},
    {FIO:'Иванов Б.Б.',mark:3.4},
    {FIO:'Сидоров Г.Г.',mark:9},
    {FIO:'Немолодой Д.Д',mark:2},
    {FIO:'Молодой Е.Е',mark:3.4}
];

let s = 0;
let kol = 0;
let BadStudents = [];

for (let i=0; i < Students.length; i++)
{
    if (Students[i].mark>5) 
    console.log('Это значение учитываться не будет оно не соответствует допустимым значениям');

    if (Students[i].mark<0) 
    console.log('Это значение учитываться не будет оно не соответствует допустимым значениям');

    if (!(Students[i].mark<=5&&Students[i].mark>=0)) 
    continue;

    if (Students[i].mark<4) 
    BadStudents.push(Students[i])

    s += Students[i].mark;
    kol = kol + 1 ;
}

s = s/kol;
console.log('Средняя оценка: '+s);
console.log('Плохие студенты:');

if(BadStudents.length === 0 ) 
console.log('Таких нет');

BadStudents.forEach((a)=> {console.log('Фио: '+a.FIO+'; Оценка: '+a.mark)});

```

### Задание 5

Необходимо просмотреть свой код из предыдущей лабораторной работе  
и провести работу над ошибками (если, конечно, ошибки есть)