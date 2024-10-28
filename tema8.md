# Тема 8. Введение в ООП
Отчет по Теме #8 выполнил(а):
- Федоткина Екатерина
- АИС-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
Создайте класс “Car” с атрибутами производитель и модель. Создайте объект этого класса. Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями.

```python
# Определяем класс "Car"
class Car:
    def __init__(self, manufacturer, model):
        # Инициализация атрибутов класса
        self.manufacturer = manufacturer  # Произведитель машины
        self.model = model  # Модель машины
# Создаем объект класса Car
my_car = Car("Toyota", "Corolla")
# Выводим информацию о машине
print(f"Бренд: {my_car.manufacturer}, Модель: {my_car.model}")
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.1.png)

## Выводы
Код демонстрирует простой пример создания класса и объекта, а также доступа к его атрибутам.

## Лабораторная работа №2
Дополните код из первого задания, добавив в него атрибуты и методы класса, заставьте машину “поехать”. Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями и получившийся вывод в консоль.

```python
class Car:
    def __init__(self, manufacturer, model):
        self.manufacturer = manufacturer  # Произведитель машины
        self.model = model  # Модель машины
        self.is_moving = False  # Флаг движения, изначально машина стоит на месте
    def drive(self):
        # Метод, заставляющий машину ехать
        if not self.is_moving:  # Если машина не движется
            self.is_moving = True  # Меняем состояние движения на "движется"
            print(f"{self.manufacturer} {self.model} движется.")  # Обратная связь о движении
        else:
            print(f"{self.manufacturer} {self.model} едет.")
    def stop(self):
        # Метод, останавливающий машину
        if self.is_moving:  # Если машина движется
            self.is_moving = False  # Меняем состояние на "остановлена"
            print(f"{self.manufacturer} {self.model} остановлена.")
        else:
            print(f"{self.manufacturer} {self.model} стоит.")
# Создаем объект класса Car
my_car = Car("Toyota", "Corolla")
my_car.drive()  # Машина начинает движение
my_car.stop()   # Машина останавливается
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.2.png)

## Выводы
Код реализует простую модель управления состоянием движения автомобиля.

## Лабораторная работа №3
Создайте новый класс “ElectricCar” с методом “charge” и атрибутом емкость батареи. Реализуйте его наследование от класса, созданного в первом задании. Заставьте машину поехать, а потом заряжаться.
 Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями и получившийся вывод в консоль.

```python
class Car:
    def __init__(self, manufacturer, model):
        self.manufacturer = manufacturer
        self.model = model
    def drive(self):
        print(f"{self.manufacturer} начинает движение.")
class ElectricCar(Car):
    def __init__(self, manufacturer, model, battery_capacity):
        super().__init__(manufacturer, model)
        self.battery_capacity = battery_capacity
    def charge(self):
        print(f"{self.manufacturer} с емкостью батареи заряжается.")
my_electric_car = ElectricCar("Tesla", "Model S", 100)
my_electric_car.drive()
my_electric_car.charge()
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.3.png)

## Выводы
В данном коде продемонстрировано наследование.

## Лабораторная работа №4
Реализуйте инкапсуляцию для класса, созданного в первом задании. Создайте защищенный атрибут производителя и приватный атрибут модели. Вызовите защищенный атрибут и заставьте машину поехать. Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями и получившийся вывод в консоль.

```python
class Car:
    def __init__(self, manufacturer, model):
        self._manufacturer = manufacturer  # Защищенный атрибут для производителя
        self.__model = model  # Приватный атрибут для модели
        self.is_moving = False  # Флаг движения, изначально машина стоит на месте
    def drive(self):
        if not self.is_moving:
            self.is_moving = True
            print(f" {self._manufacturer} {self.__model} едет.")
    def stop(self):
        if self.is_moving:
            self.is_moving = False
            print(f"The {self._manufacturer} {self.__model} стоит.")
# Создаем объект класса Car
my_car = Car("Ford", "Mustang")
my_car.drive()  # Машина начинает движение
print(f"Бренд: {my_car._manufacturer}")  # Доступ к защищенному атрибуту
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.4.png)

## Выводы
- Используются защищенные (_) и приватные (__) атрибуты для инкапсуляции данных.
- Реализуются методы для управления состоянием объекта (движение/остановка).
- Демонстрируется доступ к защищенным атрибутам.

## Лабораторная работа №5
Реализуйте полиморфизм создав основной (общий) класс “Shape”, а также еще два класса “Rectangle” и “Circle”. Внутри последних двух классов реализуйте методы для подсчета площади фигуры. После этого создайте массив с фигурами, поместите туда круг и прямоугольник, затем при помощи цикла выведите их площади. Напишите комментарии для кода, объясняющие его работу. Результатом выполнения задания будет листинг кода с комментариями и получившийся вывод в консоль.

```python
import math
# Базовый класс Shape
class Shape:
    def area(self):
        pass  # Определим этот метод в дочерних классах
# Класс Rectangle наследует Shape
class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    def area(self):
        return self.width * self.height  # Площадь прямоугольника
# Класс Circle наследует Shape
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    def area(self):
        return math.pi * (self.radius ** 2)  # Площадь круга
# Создаем массив с фигурами
shapes = [Rectangle(4, 5), Circle(3)]
# Выводим площади всех фигур
for shape in shapes:
    print(f"Площадь: {shape.area()}")  # Вызываем метод area для каждой фигуры
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.5.png)

## Выводы
В коде применяются основные принципы ООП, такие как абстракция, наследование и полиморфизм, для решения задачи расчета площадей различных фигур.

## Самостоятельная работа №1
Самостоятельно создайте класс и его объект. Они должны отличаться, от тех, что указаны в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
my_book = Book("1984", "George Orwell")
print(f"Title: {my_book.title}, Author: {my_book.author}")
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.6.png)

## Выводы
Код демонстрирует основы создания простого класса и работы с его экземпляром.

## Самостоятельная работа №2
Самостоятельно создайте атрибуты и методы для ранее созданного класса. Они должны отличаться, от тех, что указаны в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
        self.is_reading = False
    def start_reading(self):
        self.is_reading = True
        print(f"Started reading '{self.title}' by {self.author}.")
    def stop_reading(self):
        self.is_reading = False
        print(f"Stopped reading '{self.title}'.")
my_book = Book("1984", "George Orwell")
my_book.start_reading()
my_book.stop_reading()
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.7.png)

## Выводы
Данный код демонстрирует простую реализацию класса Book с методами для отслеживания процесса чтения книги.

## Самостоятельная работа №3
Самостоятельно реализуйте наследование, продолжая работать с ранее созданным классом. Оно должно отличаться, от того, что указано в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

    def start_reading(self):
        print(f"Вы начали читать '{self.title}'  {self.author}.")

class EBook(Book):
    def __init__(self, title, author, format):
        super().__init__(title, author)
        self.format = format

    def display_format(self):
        print(f"Формат '{self.title}'  {self.format}.")

my_ebook = EBook("1984", "George Orwell", "PDF")
my_ebook.start_reading()
my_ebook.display_format()
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.33.png)

## Выводы
Класс EBook наследует класс Book и добавляет новый атрибут для хранения формата (например, PDF или EPUB).


## Самостоятельная работа №4
Самостоятельно реализуйте инкапсуляцию, продолжая работать с ранее созданным классом. Она должна отличаться, от того, что указана в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.__author = author
    def get_author(self):
        return self.__author
    def set_author(self, author):
        self.__author = author
my_book = Book("1984", "George Orwell")
print(f"Автор: {my_book.get_author()}")
my_book.set_author("Eric Arthur Blair")
print(f"Новый автор: {my_book.get_author()}")
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.44.png)

## Выводы
Добавляем инкапсуляцию в класс Book, сделав атрибут автора приватным. В этом случае мы создадим методы, чтобы получать и изменять значение этого атрибута.

## Самостоятельная работа №5
Самостоятельно реализуйте полиморфизм. Он должен отличаться, от того, что указан в теоретическом материале (методичке) и лабораторных заданиях. Результатом выполнения задания будет листинг кода и получившийся вывод консоли.

```python
class Media:
    def get_description(self):
        pass
class Book(Media):
    def __init__(self, title, author):
        self.title = title
        self.__author = author
    def get_description(self):
        return f"Книга: '{self.title}' автор {self.__author}"
class EBook(Media):
    def __init__(self, title, author, format):
        self.title = title
        self.__author = author
        self.format = format
    def get_description(self):
        return f"Электронная книга: '{self.title}' автор {self.__author}, формат: {self.format}"
media_collection = [
    Book("1984", "George Orwell"),
    EBook("Sapiens", "Yuval Noah Harari", "PDF")
]
for media in media_collection:
    print(media.get_description())
```
### Результат.
![image](https://github.com/KaterinaFed9/software-engineering/blob/main/pic%7C/8.10.png)

## Выводы
Создадется базовый класс Media, а также два подкласса Book и EBook, добавляется метод get_description, который будет возвращать информацию о том, что это за медиа обьект.

## Общие выводы по теме

### 1. Основные принципы ООП
- Инкапсуляция: Этот принцип заключает в себе сокрытие внутренней реализации объекта и предоставление универсальных интерфейсов для взаимодействия с ним. Это помогает защитить данные и снизить сложность кода.
- Наследование: Позволяет создавать новые классы на основе существующих, повторно используя и расширяя функциональность. Это способствует облегчению повторного использования кода и поддержанию иерархии классов.
- Полиморфизм: Обеспечивает возможность использования объектов с одинаковым интерфейсом, независимо от их конкретного типа. Это позволяет создавать общие интерфейсы для различных реализаций, что делает код более гибким и масштабируемым.

### 2. Структура классов и объектов
- Классы представляют собой шаблоны для создания объектов и могут содержать атрибуты и методы. Объекты, в свою очередь, являются экземплярами классов, содержащими конкретные значения атрибутов и реализующие методы.

### 3. Базовые конструкции
- В Python классы создаются с использованием ключевого слова class, методы внутри классов определяются с помощью def, и атрибуты инициализируются в методе __init__.
- Применение специальных методов (например, __str__, __repr__) позволяет улучшить взаимодействие с объектами при выводе и отображении информации.

### 4. Переопределение методов и модификация поведения
- Переопределение методов (особенно в наследниках) позволяет изменять поведение классов, что способствует созданию более адаптивных и специализированных структур данных.
