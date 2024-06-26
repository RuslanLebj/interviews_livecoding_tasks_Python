# Что такое генератор?

Генератор – это итератор, элементы которого можно итерировать только 1 раз

* Элементы генератора итерируются только 1 раз, потому что они не хранятся в памяти все вместе, а создаются на лету
* Генераторы это способ реализации итераторов
* Генератор можно реализовать как функцию или как выражение

## Выражение генаратор (Generator Expressions)

Выглядят также как генераторы списка, только не в [] а в ()

```
my_generator = (i for i in range(10))
```

## Функция генератор

* Для возврата значения функция использует не return a yield

```
def generator():
    for i in range(2):
        yield i
```

В объекте генераторе определены методы iter и next, то есть реализован протокол итератора, то есть по сути любой генератор является итератором. Концептуально, итератор — это механизм поэлементного обхода данных, а генератор позволяет отложено создавать результат при итерации.

Генератор может создавать результат на основе какого-то алгоритма или брать элементы из источника данных (коллекция, файлы, сетевое подключения и пр.) и изменять их.

Ярким пример являются функции range и enumerate

range генерирует ограниченную арифметическую прогрессию целых чисел, не используя никакой источник данных.

enumerate генерирует двухэлементные кортежи с индексом и одним элементом из итерируемого объекта.

### Итог - Что такое генератор?

С точки зрения реализации, генератор в Python — это языковая конструкция, которую можно реализовать двумя способами: как функция с ключевым словом yield или как генераторное выражение. В результате вызова функции или вычисления выражения, получаем объект-генератор типа types.GeneratorType. Канонический пример - генератор, порождающий последовательность чисел Фибоначчи, которая, будучи бесконечна, не смогла бы поместиться ни в одну коллекцию. Иногда термин применяется для самой генераторной функции, а не только объекта, возвращенного ей в качестве результата.

Так как в объекте-генераторе определены методы __next__ и __iter__, то есть реализован протокол итератора, с этой точки зрения, в Python любой генератор является итератором.

Когда выполнение функции-генератора завершается, возникает исключение StopIteration.

* *Главное отличие yield от return это то, что yield, после возврата объекта, сохраняет стек генератора, так что при следующем вызове функции next() от генератора, исполнение кода генератора продолжится с того момента, где yield вернул объект в прошлый раз.