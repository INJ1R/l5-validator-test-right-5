## Правила и регламент

- [Экзамен: правила, рекомендации и порядок проведения](https://hexly.notion.site/d9289c18871c44508bc7c7f05a51d94f)

## Задание

Ваша задача написать валидатор, в котором есть ряд методов и свойств и экспортировать его из файла *src/index.js*. Валидатор позволяет проверять аргументы на соответствие необходимым условиям, которые были заданы с помощью методов валидатора.

Пример использования:

```javascript
// создаем экземпляр валидатора
const v = new Validator();
// определяем метод для валидации строк и связываем его с валидатором, обращаясь к нему через переменную.
const schema = v.string();

// проверяем данные на соответствие строковому типу, с помощью метода isValid()
schema.isValid('Hexlet'); // true
schema.isValid(''); // true
schema.isValid(null); // false
schema.isValid(123); // false
```

### Примечания

Вы можете самостоятельно протестировать работу валидатора. В каталоге *src* разрешено использовать любые файлы и создавать новые, если это делает вашу разработку более удобной.

Для тестирования валидатора, достаточно создать экземпляр валидатора, настроить валидацию с помощью методов и вызвать метод `validate()` с необходимым аргументом, после чего написать в терминале:

```bash
node src/index.js
```

## 1 задача

Вам необходимо создать валидатор, который способен принимать аргумент и проводить его проверку на соответствие определенным условиям. В данной задаче мы ограничиваемся валидацией только строк. Для этого в вашем валидаторе должен быть метод `string()`, который создает экземпляр валидатора строк. Этот экземпляр обладает методом `isValid()`, который принимает данные на вход и возвращает значение true или false в зависимости от того, являются ли входные данные строкой или нет.

**Параметры и методы**

- аргумент, который мы валидируем (проверяем)
- метод валидатора `string()`, который создает экземпляр валидатора строк
- метод экземпляра `isValid()`, который вызывается у экземпляра `string()`, он принимает данные на вход и валидирует

```javascript
const v = new Validator();
const schema = v.string();

schema.isValid(null); // false
schema.isValid(''); // true
schema.isValid(true); // false
schema.isValid('123'); // true
schema.isValid(0); // false
```

После добавления методов `string()` и `isValid()`, экземпляр валидатора будет проверять является ли аргумент типом данных *String*.

## 2 задача

а) Вам необходимо расширить функциональность экземпляра валидатора строк, добавив к нему метод `startsFromUpperCase()` .
При вызове метода `startsFromUpperCase()`, он добавляет дополнительную проверку,
которая будет выполняться при вызове метода `isValid()` на то, начинается ли строка с заглвной буквы.

б) Вам необходимо расширить функциональность экземпляра валидатора строк, добавив к нему метод `length()` .
При вызове метода `length()` c переданным аргументом, он добавляет дополнительную проверку,
которая будет выполняться при вызове метода `isValid()` на то, соответствует ли длина строки заданной.

в) Вам необходимо расширить функциональность экземпляра валидатора строк, добавив к нему метод `hasExclamation()` .
При вызове метода `hasExclamation()`, он добавляет дополнительную проверку,
которая будет выполняться при вызове метода `isValid()` на то, включает ли строка восклицательные знаки.

**Методы**

- метод `startsFromUpperCase()`, который вызывается у экземпляра `string()`. Он добавляет проверку первой буквы в слове на то, является ли она заглавной
- метод `length()`, который вызывается у экземпляра `string()`. Он добавляет проверку строки на соответствие заданной длине
- метод `hasExclamation()`, который вызывается у экземпляра `string()`. Он добавляет проверку строки на наличие восклицательных знаков

```javascript
const v = new Validator();

const schema1 = v.string();
schema1.isValid('hexlet'); // true;

const schema2 = v.string().startsFromUpperCase()
schema2.isValid('hexlet'); // false;
schema2.isValid(' hello?'); // false;
schema2.isValid('Hi'); // true;
schema2.isValid('!Hi'); // false;
schema2.isValid('1Hi'); // false;

const schema2 = v.string().length(5).startsFromUpperCase()
schema2.isValid('hexlet'); // false;
schema2.isValid(' hello?'); // false;
schema2.isValid('Hieee'); // true;
schema2.isValid('!Hide'); // false;

const schema2 = v.string().length(5).startsFromUpperCase().hasExclamation()
schema2.isValid('hexlet'); // false;
schema2.isValid(' hello?'); // false;
schema2.isValid('Hieee'); // false;
schema2.isValid('Hide!'); // true;
```

После добавления методов `startsFromUpperCase()`, экземпляр валидатора строк будет проверять содержит ли аргумент заглавные буквы.

## 3 задача

Вам необходимо создать валидатор массивов, добавив к нему метод `array()`. Аналогично методу `string()`, метод `array()` создает экземпляр валидатора массивов. Для валидации массива у этого экземпляра также есть метод `isValid()`, который проверяет, является ли переданный аргумент массивом.

**Методы**

- метод валидатора `array()`, который создает экземпляр валидатора массивов
- метод `isValid()`, который вызывается у экземпляра `array()`. Он проверяет является ли аргумент массивом

```javascript
const v = new Validator();
const schema = v.array();

schema.isValid([]); // true
schema.isValid({}); // false
schema.isValid(123); // false
schema.isValid('Hexlet'); // false
```

После добавления метода `array()`, экземпляр валидатора сможет проверять переданные значения на соответствие экземпляру глобального объекта Array.

## 4 задача

Вам необходимо расширить функциональность экземпляра валидатора массивов. Кроме того, что он может валидировать, является ли аргумент массивом, он должен также иметь возможность проверять, соответствует ли какой-либо из вложенных массивов указанной глубине, если бы вызван метод `maxDepth()`, аргументом в котором является число, означающее необходимую глубину массива, где 0 - это отсутствие вложенных массивов.

**Методы**

- метод `maxDepth()`, который вызывается у экземпляра `array()`. Он проверяет соответствует ли глубина вложенности в массиве заданному в `maxDepth()` аргументу. То есть в массиве не должно быть массивов с глубиной вложенности более чем значение аргумента.

```javascript
const v = new Validator();
const schema1 = v.array();
schema1.isValid([1, 2]); // true

const schema2 = v.array().maxDepth(3);
schema2.isValid([1, 2]); // true
schema2.isValid([1, [2, [3]]]); // true
schema2.isValid([1, [2, [3, [4]]]]); // false
```

После добавления метода `maxDepth()`, экземпляр валидатора массивов будет способен проверять, соответствует ли длина массива заданной в методе длине.

## 5 задача

Вам необходимо создать валидатор полей объекта, используя методы, представленные в предыдущих задачах. Для этого необходимо создать метод `object()`, который проверяет не сам объект, а данные внутри него на соответствием заданным валидаторам. Метод `Validator.object()` должен содержать метод `shape()`, позволяющий задать поля, подлежащие валидации, для объекта. Метод `shape()` принимает объект, в котором ключи представляют поля, которые требуется проверить, а значения - экземпляры валидаторов.

**Методы**

- метод валидатора (экземпляр класса *Validator*) `object()`, который проверяет данные внутри объекта (поля объекта)
- метод `shape()`, который вызывается у экземпляра `object()`. Он позволяет задать поля валидации для объекта

```javascript
const v = new Validator();

// Позволяет описывать валидацию для свойств объекта
const schema = v.object().shape({
  name: v.string().startsFromUpperCase(), // теперь, при валидации объекта с ключом id, значение этого ключа пройдет валидацию в соответствии с текущими методами
  friends: v.array().maxDepth(0),
});

schema.isValid({ name: 'Sergey', friends: ['mark', 'john', 'anna'] }); // true
schema.isValid({ name: 12, friends: ['potatos', 'tomatos', 'oranges'] }); // false
schema.isValid({ name: 'andrey', friends: ['sergey',['ivan', 'anatoly']] }); // false
```

После добавления методов `object()` и `shape()`, экземпляр валидатора сможет проверять поля объекта на соответствие заданным валидаторам