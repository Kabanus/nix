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
#### If vs Switch
```
// If по-новому
let age = Int.random(in: 0 ... 100)
print(age)
if age <= 10 {
  print("Малыш")
} else if 11...15 ~= age {
  print("Подросток")
} else if 16...20 ~= age {
  print("Студент")
} else if 21...30 ~= age {
  print("Молодой")
} else if 31...40 ~= age {
  print("Семейный")
} else if 41...60 ~= age {
  print("Опытный")
} else if age > 60 {
  print("Пожилой")
}
```
```
// If по-старому
let age = Int.random(in: 0 ... 100)
print(age)
if age <= 10{
    print("малыш")
}else if age > 10 && age <= 15{
    print("подросток")
}else if age > 15 && age <= 20{
    print("студент")
}else if age > 20 && age <= 30{
    print("молодой")
}else if age > 30 && age <= 40{
    print("семейный")
}else if age > 40 && age <= 60{
    print("опытный")
}else if age > 60 {
    print("пожилой")
}
```
```
// Switch
let age = Int.random(in: 0 ... 100)
print(age)
switch age {
case 0...10:
  print("Малыш")
case 11...15:
  print("Подросток")
case 16...20:
  print("Студент")
case 21...30:
  print("Молодой")
case 31...40:
  print("Семейный")
case 41...60:
  print("Опытный")
case 60...:
  print("Пожилой")
default:
  print("default")
}
```
# Loops // Циклы
* **for** - цикл с элементами диапазона, коллекции и пр. - перебирает все элементы
* **while** - до тех пор, пока условие = ***true*** (проверяется в начале цикла)
* **repeat-while** - до тех пор, пока условие = ***true*** (проверяется в конце цикла)
* **stride** - "шагать" - для тех, кто привык к стандартным циклам java
#### Range
```
// Closed
let digits = 0...10 // от 0 до 10 включительно
```
```
// Half-Open
let digits = 0..<10 // не включает 10
```
```
// One-Sided
let digits = ...10 // все значения меньше 10
let digits = 10... // все значения больше 10
```
#### For
```
let range = 1...10
for number in range {
  print(number, terminator: "") // печать без перехода на новую строку
  if number == 8 {break}
}
```
```
// For без переменной
for _ in 1...10 {
  print("Hello Kitty!")
}
```
```
// Вложенный цикл + break
for1: for i in 1...10 {
  for2: for j in 1...5 {
    if i % 3 == 0 {
      break for1 // если не указать метку - выход будет производиться только из внутреннего цикла
    }
    print(i,j)
  }
}
```
```
// Вложенный цикл + continue
for1: for i in 1...10 {
  for2: for j in 1...5 {
    if i % 3 == 0 {
      continue for1 // если не указать метку - выход будет производиться только из внутреннего цикла
    }
    print(i,j)
  }
}
```
#### Where
```
for i in 1..<10 where i % 3 == 0 {
  print("\(i) = ok")
}
```
#### Inner
```
var sum = 0
for number1 in 1...10 {
  sum += number1
  for number2 in 1...10 {
    sum += number2
  }
}
print(sum)
```
#### While
```
var i = 0
while i < 10{
  i += 1
  if i == 5 {
    continue
  }
  print(i)
}
```
#### Repeat-While
```
var i = 0
repeat {
  i -= 1
  print(i)
} while (i>0)
```
#### Stride
```
for i in stride(from: 10, to: 20, by: 2) { // 20 не включается
  print(i)
}
```
```
for i in stride(from: 10, through: 20, by: 2) { // 20 включается
  print(i)
}
```
```
// Обратно
for i in stride(from: 20, through: 10, by: 2) {
  print(i)
}
```
```
// 1. напечатайте все числа от 1 до 100 включительно, где есть цифра 1
for number in 1...100 where String(number).contains("1"){
  print(number)
}

// 2. распечатать с помощью цикла квадрат 5х5, используя символ #
for _ in 1...5 {
  for _ in 1...5 {
    print("# ", terminator: "")
  }
  print()
}

// 3. распечатать с помощью цикла треугольник со 2 сторонами равными 5 символам #
for x in 1...5 {
  var resultStr = ""
  for _ in 1...x {
    resultStr += "# "
  }
  print(resultStr)
}

// 4. используя while посчитайте сумму четных чисел от 1 до 100 включительно
var i = 0
var sum = 0
while i < 100 {
  i += 1
    if i % 2 == 0 {
      sum += i
      print(i, terminator: "|")
    }
}
print(sum)
```
# Optionals
* Optional - это контейнер: может содержать любой тип данных или nil
#### Извлечение
##### Явное (force unwrapping) - символ "?" при объявлении
* Извлечение значений вручную, где это необходимо в коде
* Для переменных, которые часто могут быть nil
* Для всех вариантов, где не подходит **implicit unwrapping**
##### Неявное (implicit unwrapping) - символ "!" при объявлении
* Для переменных или констант, которые нужно обязательно один раз заполнить (проинициализировать) и потом везде использовать
* Константы, которые инициализируются при создании объекта
* Позволяет НЕ выполнять извлечение значений вручную по всему коду
```
// Явное извлечение
var IntOptional1:Int? // знак "?" означает "упаковку" в контейнер (по-умолчанию присваиватся значение nil)
var IntOptional2:Optional<Int> // альтернативный вариант
var intOptional3:Int? = 10
print(intOptional3!) // Извлечение значения с помощью знака "!" (значение не должно быть пустым)
```
```
// Неявное извлечение
var str: String! // знак "!" означает "упаковку" в контейнер (по-умолчанию присваиватся значение nil)
print(str) // автоматическое извлечение значения (значения может быть пустым, но это нежелательно)
```
#### Optional Binding
```
// Извлечение значения, при наличии, из контейнера
var a:Int? = 5
if let a = a{ // let a - новая сущность доступная только внутри тела if
  print(a+5)
}
```
// Проверка наличия значения в контейнере
```
if a != nil {
  print("\(a!) not nil")
}
```
// Присвоение значения по умолчанию (coalescing)
```
var nullValue: Int?
var mainValue = nullValue ?? 0
```
#### Optional Chaining
```
var str: String?
var count = str?.characters.count // "?" - если значение str не пусто - выполнить дальнейшие действия, иначе присвоить nil
print(count)
```
