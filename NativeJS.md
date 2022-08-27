# JavaScript

# `Pазница между ключевыми словами «var», «let» и «const»:`

- переменные, объявленные с помощью ключевого слова «var», являются глобальными. Это означает, что они доступны из
  любого места в коде;
- разница между «let» и «const» состоит в том, что в первом случае мы может менять значение переменной, а во втором —
  нет (константа). При этом, мы можем менять значение свойства объекта, объявленного с помощью const, но не само
  свойство (переменную).

# `Типы данных`

## Примитивные типы данных:

- `number` \\ 1, 5.65
- `string` \\ 'hello'
- `boolean` \\ true, false
- `null` \\ null
- `undefined` \\ undefined -
- `symbol` \\ Symbol(id)
- `BigInt` \\ 1234567890123456789012345678901234567890n

### Ссылочный тип:

- `Object`  
  Оператор `typeof` возвращает тип данных. Результатом `typeof` является строка, содержащая тип:

```JS
typeof undefined    // undefined
typeof 0    // number
typeof 1n   // bigint
typeof true   // boolean
typeof 'hello'   // string
typeof Symbol()   // symbol
typeof {}   // object
typeof null   // object - признанная ошибка, которая сохраняется для совместимости (null - это не объект, а тип данных)
typeof function () {
}   // function - это подвид объекта, но typeof выделяет функции отдельно (на практике для легкого определения)
typeof typeof number // string, т.к. оператор typeof вовзращает тип в виде строки
```

# `Array methods`

- `.map()` - метод, вызывающий переданную ей функцию для каждого элемента массива и возвращает **новый массив**
  результатов этой функции

```JS
let arr = [1, 2, 3, 4, 5]
let newArray = arr.map(i => i * 2)    // result: [ 2, 4, 6, 8, 10 ]
```

- `.filter()` - метод, вызывающий переданную ей функцию для каждого элемента массива, и возвращает **новый массив**, в
  который войдут только те элементы, которые функция вернула **true**:

```JS
let arr = [10, 10, 20, 20, 10, 30, 40, 50]
let filteredArr = arr.filter(n => n === 10)
console.log(filteredArr) // [10, 10, 10]
```

- `.sort()` - метод, сортирующий массив на месте

```JS
let arr = [1, 2, 7, 9, 4, 5, 3, 6, 8, 0] // новый массив, с неупорядоченными числами
arr.sort() // вызываем метод сортировки, сортирует на месте, мутирует
console.log(arr) // ВЫВОД: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

- `.push()` - добавляет элементы в конец

```JS
let arr = [1, 2, 3]
arr.push('ELEMENT') // пушим ELEMENT  в конец массива, мутируем
console.log(arr) // ВЫВОД: [1, 2, 3, "ELEMENT"]
```

- `.pop()` - извлекает элемент из конца

```JS
let arr = [1, 2, 3]
let popNumber = arr.pop() // извлекаем последний элемент массива и сохраняем в переменной popNumber
console.log(arr) // ВЫВОД: [1, 2]
console.log(popNumber) // ВЫВОД: 3
```

- `.shift()` - извлекает элемент из начала

```JS
let arr = [1, 2, 3]
let shiftNumber = arr.shift() // извлекаем первый элемент массива и сохраняем в переменной shiftNumber
console.log(arr) // ВЫВОД: [2, 3]
console.log(shiftNumber) // ВЫВОД: 1
```

- `.unshift()` - добавляет элементы в начало

```JS
let arr = [1, 2, 3]
arr.unshift('ELEMENT') // добавляем ELEMENT  в начало массива
console.log(arr) // ВЫВОД: ["ELEMENT", 1, 2, 3]
```

- `.indexOf()` - возвращает первый индекс, по которому данный элемент может быть найден в массиве или -1, если такого
  индекса нет

В следующем примере `indexOf()` используется для поиска значений в массиве.

```JS
var array = [2, 5, 9];
array.indexOf(2);     // 0
array.indexOf(7);     // -1
array.indexOf(9, 2);  // 2
array.indexOf(2, -1); // -1
array.indexOf(2, -3); // 0
```

В следующем примере `indexOf()` используется для поиска всех индексов элемента в указанном массиве, которые с
помощью `push()` добавляются в другой массив.

```JS
var indices = [];
var array = ['a', 'b', 'a', 'c', 'a', 'd'];
var element = 'a';
var idx = array.indexOf(element);
while (idx != -1) {
    indices.push(idx);
    idx = array.indexOf(element, idx + 1);
}

console.log(indices);
// [0, 2, 4]
```

- `.slice()` - возвращает новый массив, содержащий копию части исходного массива

В следующем примере метод slice() используется для создания новой строки

```JS
let arr = [1, 2, 3]
let str1 = 'Приближается утро.';
let str2 = str1.slice(1, 8);
let str3 = str1.slice(4, -2);
let str4 = str1.slice(12);
let str5 = str1.slice(30);

console.log(str2); // ВЫВОД: риближа
console.log(str3); // ВЫВОД: лижается утр
console.log(str4); // ВЫВОД:  утро.
console.log(str5); // ВЫВОД: ""
```

# `addEventListener` - зачем нужен и у кого он есть

Метод `addEventListener` нужен для регистрации определенного отработчика события.

* Новый обработчик события **не переписывает** уже существующие обработчики событий
* Мы можем добавлять **сколько угодно** обработчиков событий одного типа ('click')
* Метод **addEventListener** мы можем повесить **на что угодно**: на button, div и даже на окно.
  `Синтаксис:`:

```JS
element.addEventListener(event, function () {
}, useCapture);
```
# `Методы функций call(), apply() и bind()`

В языке JS функции - это тоже объекты, и поэтому у них тоже есть методы:

* `.call()` - это метод, который вызывает функцию с указанным значением **this**:

```JS
// создаем объект:
let bag = {
    apple: 5
}
// пишем функцию:
function showAge() {
    console.log(this.apple) // если мы вызовем функцию без call, то ничего не получится
}
// вызываем функцию:
showAge.call(bag)  // ВЫВОД: 5 
```  

* `.aplly()` - это метод, который работат аналогичсно методу `call`, но принимает массив аргумента вместо списка:

```JS
// создаем объект:
let man = {
    name: 'Eugene',
    age: 18
}
// пишем функцию:
function showMan(sex, city) { // обратите внимание, функция принимает аргументы
    console.log(this.name + ' | ' + this.age + ' | ' + sex + ' | ' + city)
}
// вызов функции:
showMan.apply(man, ['man', 'Minsk']) // ВЫВОД: "Eugene | 18 | man | Minsk"
```  

* `.bind()` - просто **'байндит'** указанную функцию, не вызывая ее:

```JS
let user = {
    name: "Eugene"
};
function func() {
    console.log(this.name);
}
let funcName = func.bind(user);
funcName(); // ВЫВОД: 'Eugene'
```  