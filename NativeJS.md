# JavaScript

# `Pазница между ключевыми словами «var», «let» и «const»:`

- переменные, объявленные с помощью ключевого слова «var», являются глобальными. Это означает, что они доступны из любого места в коде;
- разница между «let» и «const» состоит в том, что в первом случае мы может менять значение переменной, а во втором — нет (константа). При этом, мы можем менять значение свойства объекта, объявленного с помощью const, но не само свойство (переменную).

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