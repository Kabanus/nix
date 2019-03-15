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
#### Optional Chaining
```
var str: String?
var count = str?.count // "?" - если значение str не пусто - выполнить дальнейшие действия, иначе присвоить nil
var count = str!.count // "!" - извлечь значение в любом случае, если значения нет - ошибка
print(count)
```
#### NilCoalescing
```
// Присвоение значения по умолчанию
var nullValue: Int?
var mainValue = nullValue ?? 0
```
#### Optional Tuples
```
// Опциональный кортеж
var optTuple: (Int, str:String)? = (6, "text")
print(optTuple!.0)
print(optTuple!.str)
```
```
// Опциональные значения кортежа
var optTupleValues: (Int?, String?) = (1, "text2")
print(optTupleValues.0!)
print(optTupleValues.1!)
```
```
// Опциональный кортеж и опциональные значения
var optTupleWithValues: (Int?, String?)? = (3, "text3")
print(optTupleWithValues!.0!)
print(optTupleWithValues!.1!)
```
```
Неявное извлечение "!" возможно только для всего кортежа, а не для его отдельных элементов
```
#### Convert
```
// При конвертации в Int/Double возвращается Optional, если конвертация не удается - возвращается nil
// При конвертации в String возвращается String
var strValue = "0"
var intValue = 10
let intVal = Int(strValue)
type(of: intVal)
print(intVal!)
```
#### Optional Switch
```
let str: String? = "text"
switch (str) {
case .none:
  print("no text")
case .some (let txt):
  print("text is: \(txt)")
}
```
#### Optional Inner
```
// Контейнер внутри контейнера
let constVal: String????? = "text"
print(constVal!!!!!)
```
#### Binding Chaining
```
// Optional Binding + Optional Chaining
var str:String? = "text"
if let count = str?.count {
  print(count)
}else{
  print("count is nil")
}
```
```
// Без Optional Chaining
var str:String? = "text"
if str != nil {
  let count = str!.count
  print(count)
}else{
  print("count is nil")
}
```
```
// Распечатать в одну строку все буквы из текста, исключая пробелы
var text:String? = "Swift has built-in support for checking API availability, which ensures that you don’t accidentally use APIs that are unavailable on a given deployment target"
for char in text! {
  if char != " "{
    print(char, terminator: "")}
}
```
# Функции
* Функция - непривязана, автономна (не относится к объекту)
* Метод - функция внутри определенного типа (class, struct, enum)
* Функция:
  * может возврящать значение (любой тип)
  * не может возвращать значение - () или Void
* Функцию можно объявлять внутри другой функции (Nested Function)
#### Объявление функции без параметров
```
func printReady(){
  print("ready")
}
printReady()
```
#### Объявление функции с параметрами
```
func sendParam(str: String, index: Int){ // параметры являются константами
  print(str,index)
}
sendParam(str: "text", index: 1) // при вызове имена параметров обязательны
```
#### Объявление функции с возвратом результата
```
func sum(int1: Int, int2: Int) -> Int{
  return int1+int2;
}
print(sum(int1: 2, int2: 5))
```
#### Объявление функции без возврата результата
```
func returnVoid1() -> Void{ // Void лучше ()
  print("void")
}
func returnVoid2() -> (){
  print("void")
}
func returnVoid3(){
  print("void")
}
returnVoid1()
returnVoid2()
returnVoid3()
```
#### Значение по-умолчанию для параметров
```
func useDefaultValues(str: String = "default", index: Int = 5){
  print(str,index)
}
useDefaultValues()
useDefaultValues(str: "hello", index: 10)
```
#### InOut
```
// функция измененяет значения внешней переменной
// (параметр метода хранит ссылку на переменную, а не копию значнения)
// в этом случае параметр функции - не константа
func inOutFunc(index: inout Int){
  index += 1
}
var indexVar = 7
inOutFunc(index: &indexVar)
print(indexVar)
```
#### Label
```
// метка - не имя переменной, а ее более подробное описание
// если не указать метку - она автоматически создастся от имени параметра
func convertText(textForConversion text: String, index: Int){
  print(text,index)
}
convertText(textForConversion: "new text", index: 1)
```
```
// отключение меток
func omitLabels(_ p1: Int, _ p2: Int, str: String){
  print(p1,p2)
}
omitLabels(5,7, str: "text")
```
#### Функция с возвратом кортежа
```
func sum(int1: Int, int2: Int) -> (Int, String) {
  return (int1 + int2, "success")
}
print(sum(int1: 2, int2: 5))
var tupleResult = sum(int1: 10, int2: 20)
print(tupleResult.0) // первый элемент кортежа - 30
print(tupleResult.1) // второй элемент кортежа - success
```
```
// Вовзрат кортежа с параметром типа кортежа
func funcTuple(tupleParam p: (Int, Int)) -> (Int, String) {
  return (p.0 + p.1, "success")
}
print(funcTuple(tupleParam: (2, 5)))
```
```
// Добавить имена параметров возвращаемого кортежа
func sum2(tupleParam p: (Int, Int)) -> (sum: Int, result: String) {
  return (p.0 + p.1, "success")
}
var sumTuple = sum2(tupleParam: (2,5))
print(sumTuple.result)
print(sumTuple.sum)
```
#### FuncAsVar
```
// Присваивание функции в переменную
func addStrValue (_ str: String) -> String {
  return str + " added value"
}
// var addStrMethod: (String) -> String = addStrValue
var addStrMethod = addStrValue
print(addStrMethod("new"))
```
```
// Присваивание функции в переменную (с подходящими параметрами и возвращаемым значением)
func sum(_ int1: Int, _ int2: Int) -> Int {
  return int1 + int2
}
var sumMethod: (Int, Int) -> Int = sum
print(sumMethod(1,2))
```
#### FuncAsReturn
```
// Функция, как тип возвращаемого значения другой функции
func plus(p1: Int, p2: Int) -> Int {
  return p1 + p2
}
func minus(p1: Int, p2: Int) -> Int {
  return p1 - p2
}
// возврат функции в зависимости от параметра
func returnFuncType(oper: Bool) -> (Int, Int) -> Int {
  if oper {
    return plus
  } else {
    return minus
  }
}
// сначала возвращается функция, затем она вызывается с параметрами
print(returnFuncType(oper: true)(5,2))
print(returnFuncType(oper: false)(5,2))
```
#### FuncAsParam
```
func sum(p1: Int, p2: Int) -> Int {
  return p1 + p2
}
func extract(p1: Int, p2: Int) -> Int {
  return p1 - p2
}
func funcParam(funcType: (Int, Int) -> Int, _ a: Int, _ b: Int) {
  print(funcType(a,b))
}
funcParam(funcType: sum, 2,5)
funcParam(funcType: extract, 5,1)
```
#### Optional
```
func testParamOptional(str: String?) {
  if let str = str {
    print(str)
  }
}
testParamOptional(str: nil)
```
```
// Optional в возвращаемом типе
func testReturnOptional(str: String) -> Int? {
  return str.count
}
print(testReturnOptional(str: "test")!)
```
```
// Optional в возвращаемом типе и параметре
func testAllOptional(str: String?) -> Int? {
  return str?.count
}
print(testAllOptional(str: "test")!)
```
```
// implicit unwrapping
func testImplicitOptParam(str: String!) -> Int {
  return str.count
}
var a: String? = "test"
print(testImplicitOptParam(str: a))
```
#### NestedFunc
```
func returnFuncType(oper: Bool) -> (Int, Int) -> Int {
  var result: String
  // внутренние функции имеют доступ к переменным внешней функции
  func plus (p1: Int, p2: Int) -> Int {
    return p1 + p2
  }
  func minus (p1: Int, p2: Int) -> Int {
    return p1 - p2
  }
  if oper {
    return plus
  } else {
    return minus
  }
}
print(returnFuncType(oper: true)(5,2))
print(returnFuncType(oper: false)(5,2))
```
#### Overload
* Overloading - перезагрузка функции (метода) - название совпадает, но параметры и тип возвращаемого значения могут отличаться
```
func plus (p1: Int, p2: Int) -> Int {
  return p1 + p2
}
func plus (p1: Double, p2: Double) -> Double {
  return p1 + p2
}
func plus () {
  print("void")
}
print(plus(p1: 10, p2: 20))
print(plus(p1: 30.3, p2: 40.4))
plus()
```
#### TypeAlias
```
typealias MethodType = (String, Bool, Int) -> (Int, String, Bool, String)
func newMethod (_ str: String, _ b: Bool, _ i: Int) -> (Int, String, Bool, String) {
  print (str, b, i)
  return (i, "test", true, "test2")
}
var printVar: MethodType = newMethod
print(printVar("test", true, 1))
```
```
// функция, как параметр другой функции
func sum (_ i1: Int, _ i2: Int) -> Int {
  return i1 + i2
}
typealias SumType = (Int, Int) -> Int
var sumMethod: SumType = sum
func secondFunc (_ sumMethod: SumType, _ a: Int, _ b: Int) {
  print(sumMethod(a, b))
}
secondFunc(sum, 10, 20)
```
```
/* 1) реализуйте функцию, которая принимает String, конвертирует их в числа и возвращает сумму
Если значение любого параметра равно nil - конвертируем в 0
Если конвертация одного из параметров не проходит - конвертируем в 0 */

func convertParams(str1:String?, str2:String?, str3:String?) -> Int? {
  var sum: Int?
  let n1 = Int(str1 ?? "") ?? 0
  let n2 = Int(str2 ?? "") ?? 0
  let n3 = Int(str3 ?? "") ?? 0
  sum = n1 + n2 + n3
  return sum
}

// для проверки

var success = convertParams(str1: "6", str2: "22", str3: "123");

var fail = convertParams(str1: "asd", str2: "22", str3: "123");

var successWithNil = convertParams(str1: nil, str2: "56", str3: "251");

if let sum = success {
    print(sum)
}else{
    print("fail")
}

if let sum = fail {
    print(sum)
}else{
    print("fail")
}

if let sum = successWithNil {
    print(sum)
}else{
    print("fail")
}
```
```
/* 2) та же функция, но:
Если значение любого параметра равно nil - выходим из функции и возвращаем nil
Если конвертация одного из параметров не проходит - выходим из функции и возвращаем nil */

func convertParams(str1:String?, str2:String?, str3:String?) -> Int? {
  var sum:Int?
  // проверяем переданные параметры
  if1: if let str1 = str1, let str2 = str2, let str3 = str3{
    // проверяем результаты конвертаций
    if let n1 = Int(str1), let n2 = Int(str2), let n3 = Int(str3){
      sum = n1 + n2 + n3
    }else{
      //  выходим из всех условий
      break if1
    }
  }
  return sum
}

// для проверки

var success = convertParams(str1: "6", str2: "22", str3: "123");

var fail = convertParams(str1: "asd", str2: "22", str3: "123");

var successWithNil2 = convertParams(str1: nil, str2: "56", str3: "251");

if let sum = success {
    print(sum)
}else{
    print("fail")
}

if let sum = fail {
    print(sum)
}else{
    print("fail")
}

if let sum = successWithNil2 {
    print(sum)
}else{
    print("fail")
}
```
# Замыкания / Closure
* Closure - анонимная функция, без слова func
```
let testClosure1:() -> () = {
  print("test")
}
let testClosure2:() -> Void = {
  print("test")
}
let testClosure3 = {
  print("test")
}
testClosure1()
testClosure2()
testClosure3()
```
```
// Замыкание с параметром
var printNumber: (Int) -> () = { (number) in
  print(number)
}
printNumber(5)
```
```
// Замыкание с параметром и возвращаемым значением
var printTextAndNumber: (Int, String) -> (String) = { (number, text) in
  return "\(text): \(number)"
}
print(printTextAndNumber(5, "test text"))
```
```
// Замыкание для подсчета суммы
var sum1: (Int, Int) -> Int = { (number1, number2) in
  return number1 + number2
}
// параметры без скобок
var sum2: (Int, Int) -> Int = { number1, number2 in
  return number1 + number2
}
// без указания параметров и in
var sum3: (Int, Int) -> Int = { return $0 + $1}
// без return
var sum4: (Int, Int) -> Int = { $0 + $1 }

print(sum1(1,2))
print(sum2(3,4))
print(sum3(5,6))
print(sum4(7,8))
```
```
// Работа с переменной, а не с константой
var testConst: (String) -> String = {
  var str = $0
  str.append(" - new text")
  return str
}
print(testConst("base text"))
```
