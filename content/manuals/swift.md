# Константы и переменные
#### Объявление константы
```
let c1 = 1
let c2:Int = 2
```
#### Объявление переменной
```
var v1 = 3.0 as Double
var v2:String = text
```
#### Изменение переменной
```
var v3 = "text"
v3 = "new text"
```
#### Объявление в одну строку
```
let one, two, three: Int
var four = 4, five = 5, six = 6
```
#### Узнать тип
```
type(of: c1)
```
#### Конвертация типа
```
var v1 = 1
var v2 = 2.0
var v3 = v1 + Int(v2)
```
#### Вывести значение
```
print(v1)
print("Hello Kitty! \(v1)")
```
#### Инкремент
```
v1 = v1 + 1
v1 += 1
```
#### "Верблюжья" нотация именования
```
let someConstName:Int // переменные с маленькой буквы
typealias MyString = String // алиасы с большой буквы
```
#### Комментарии
```
// - Линия
/* */ - Блок
```
#### Массив // Array
```
Индексы : Значения
```
#### Словарь // Dictionary
```
Ключи : Значения
```
#### Множество // Set
```
Значения
```
#### Кортеж // Tuple
```
Группы значений
```
# Типы данных
#### Value Type - значение
* Сравнение через == (сравнивается значение)
* При присвоении или передаче в функции - создается копия значения
* Пример: Int, Double, String, Array, Dictionary, Set, Struct, Tuple
#### Reference Type - ссылка на объект / область памяти
* Cравнение через === (ссылка на объект)
* При присвоении или передаче в функции - копируется ссылка на объект
* Пример: создаваемые объекты в коде и ссылки на них
#### Многострочное значение
```
let c1 = """
Hello
Kitty
"""
```
#### Подстрока // Substring
```
let c1 = "123"
let c2 = c1.dropLast(2) // отбросить два последних символа
```
#### Алиас // Alias
```
typealias MyString = String
typealias PersonTuple = (firstName: String, secondName: String, age: Int, car: Bool)
var personIvan: PersonTuple = ("Ivan", "Ivanov", 20, false)
```
#### Количество символов в строке
```
let c1 = "Hello, Kitty!"
print(c1.count)
```
#### Индексы
```
let c1 = "Hello, Kitty!"
let index = c1.index(of: ",") ?? c1.endIndex
print(c1[..<index])
print(c1[index...])
```
# Кортежи // Tuples
```
let c1 = ("text", 1)
print(c1.0) // обращение по индексу
var v1 = (a: "text", b: 1) // кортеж с метками
print(v1.b) // обращение по метке
let (x, y, z) = (1, 2, 3) // массовое объявление переменных
var person: (firstName: String, secondName: String, age: Int) = ("Ivan", "Ivanov", 25)
```
#### Поменять значения двух переменных с помощью кортежа
```
var a = 1
var b = 2
(a, b) = (b ,a)
```
# Условные операторы
* if else - простые условия
* switch - много условий
* guard - ранний выход
#### if else
```
let letterA = "A"
if letterA == "A" {
  print(true)
} else if letterA == "B" {
  print("else1")
} else {
  print("false")
}
```
```
if letterA != "A" {
  print("not a")
}
```
```
? - if
: - else
let letterB = "B"
letterB == "B" ? print("true B") : print("not B")
let letters = letterA + (!letterB.isEmpty ? letterB : "")
print(letters)
```
#### Switch
```
let text: String = "test55"
switch text {
case "test":
  print("1")
case "test2", "test3":
  print("2")
default:
  print("true default 1")
}
```
#### Where
```
var a = 11
switch a {
case _ where a % 3 == 2: // _ (нижнее подчеркивание) - любое значение
  print(a)
default:
  print("")
}
```
#### Fallthrough
```
var a = 2
switch a {
case 1:
  print("a=1")
  fallthrough
case 2:
  print("a=2")
  fallthrough
case 3:
  print("a=3")
default:
  print("default")
}
```
```
var a = 17
switch a {
case 1..<10:
  print("<10")
case 10..<20:
  print(">10")
case 20..<30:
  print(">20")
default:
  print("")
}
```
```
let letters = (a: "А", b: "Б", c: "Ц", d: "Д", e: "Е")
switch letters {
case (_, _, _, _, _):
  print("Любые значения")
case ("А", _, _, _, _):
  print("Найдена А")
case (_, _, "Ц", _, "Е"):
  print("Найдены Ц и Е")
default:
  print("default")
}
```
