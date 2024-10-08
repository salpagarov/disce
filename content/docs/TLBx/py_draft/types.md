## Типы данных

### Отсутствующее значение

Отсутствие результата тоже результат. Этой банальной сентенцией объясняется наличие в Python значения `None`.

~~~python
>>> None
>>> 
~~~

Любое действие, не предполагающее возвращаемого значения, на самом деле возвращает `None`. Это не нулевое значение, это именно "ничто".

`print` - забегая вперед, скажем, что это функция - выводит в консоль то, что получает в качестве параметра, но возвращает именно `None`.

~~~python
>>> print(print(4))
4
None
>>>
~~~

В описанном примере функция `print` печатает `4` и это работает как в интерактивном режиме, так и в пакетном. А вот возвращает она `None` и это можно увидеть, только напечатав то, что возвращает вложенный вызов `print`. 

### Логические значения

Их два - `True` и `False` ("истина" и "ложь" соответственно).

~~~python
>>> True             # истина
True
>>> not True         # ложь - это НЕ истина
False
>>> True or False    # это ложь ИЛИ истина (так и есть; высказывание верно)
True
>>> True and False   # это ложь и истина одновременно (так не бывает; высказывание ложно)
False
>>> True | False     # другая запись для OR
True
>>> True & False     # другая запись для AND
False
~~~

Все это довольно просто, даже если вы не знакомы с математической логикой и кругами Эйлера (кстати, почему?).

### Целые числа

Целое число состоит из цифр и, если нужно, знака "-" (в отличие от натуральных, они могут быть и отрицательными).

~~~python
>>> 2+2           # сложение
4
>>> 2-6           # вычитание (целые числа могут быть и отрицательнами)
-4
>>> 2*2           # умножения
4
>>> 2**2          # возведение в степень
4
>>> 8//2          # челочисленное деление (без дробной части)
4
>>> 5 % 2         # остаток от целочисленного деления
1
>>> 2+2*2         # привычные со школы приоритеты операций
6
>>> (2+2)*2       # которые можно переопределять скобками
8
~~~
Целые числа в Python могут быть любой длины. Для них в интерпретаторе реализована так называемая "длинная арифметика", щедрый подарок любителям астрономии и криптографии.

~~~python
>>> 2**2048
32317006071311007300714876688669951960444102669715484032130345427524655138867890893
19720141152291346368871796092189801949411955915049092109508815238644828312063087736
73009960917501977503896521067960576383840675682767922186426197561618380943384761704
70581645852036305042887575891541065808607552399123930385521914333389668342420684974
78656456949485617603532632205807780565933102619270846031415025859286417711672594360
37184618573575983511523016459044036976132332872312271256847108202097251571017269313
23469678542580656697935045997268352998638215525166389437335543602135433229604645318
478604952148193555853611059596230656
~~~

Числа можно сравнивать. При этом результат логическом операции сравнения будет логическое выражение.

~~~python
>>> 2 == 3        # выражение ложно потому, что два НЕ равно трем
False
>>> 2 != 3        # выражение истино потому что два НЕ РАВНО трем
True
>>> not 2 == 3    # выражение истино, потому что оно отрицает ложное сравнение разных чисел
True
>>> 2 > 3         # два больше трех (неправда!)
False
>>> 2 < 3         # два меньше трех (а вот это верно)
True
~~~

### Вещественные числа

Вы могли заметить, что в списке операций не было деления. "Настоящего", не целочисленного. Оно есть, но к целым числам неприменимо, потому что результат такого деления может быть дробным. Так что, перед выполнением деления целые числа будут сначала преобразованы в вещественные. А это уже совсем другое дело.

Целая часть вещественного числа вместо запятой отделяется от дробной "десятичной точкой", как это принято в западной математической традиции.

~~~python
>>> 4/2         # результат операции деления всегда вещественный, даже если дробная часть равна нулю
2.0
>>> 2**2048/2   # а на вещественные числа прелести длинной арифметики не распространяются
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
OverflowError: integer division result too large for a float
~~~

В отличие от целых чисел, размер которых ограничен лишь количеством оперативной памяти, вещественные занимают а памяти строго по 8 байт. 

~~~python
>>> 2**1024//2  # кажется, здесь нас тоже ждет проблема
89884656743115795386465259539451236680898848947115328636715040578866337902750481566354238661203768010560056939935696678829394884407208311246423715319737062188883946712432742638151109800623047059726541476042502884419075341171231440736956555270413618581675255342293149119973622969239858152417678164812112068608
>>> 2**1024/2   # или нет?
8.98846567431158e+307
~~~

Все не так плохо, на самом деле. Вещественные числа хранятся в экспоненциальной форме. Сравните первые цифры, они совпадают. Так вот, приставка e+307 означает "умножить на 10 в степени 307". Сдвинуть десятичную точку на 307 знаков вправо и получаем то же самое. Ну, примерно.

~~~python
>>> .42e2     # нуль перед точкой можно и не писать
42.0
>>> 42000e-3  # играть с десятичной точкой можно как угодно
42.0
~~~

Точность, конечно, оставляет желать лучшего. С вещественными числами вообще нужно обращаться с осторожностью.

~~~python
>>> .2
0.2
>>> .2+.2
0.4
>>> .2+.2+.2
0.6000000000000001
>>> .2+.2+.2+.2
0.8
~~~

Python тут не при чем, в других языках программирования то же самое. Это проблема реализации операций с "плавающей запятой" в процессоре. 

### Комплексные числа

Вспомните ли вы, когда вам приходилось работать с комплексными числами после университета? Но Гвидо ван Россум решил, что это настолько повседневно используемая сущность, что внес ее непосредственно в язык.

~~~python
>>> 42+0j  # все то же число с нулевой мнимой частью
(42+0j)
>>> >>> (40.5+0j)+1.5  # комплексные числа могут быть дробными, с ними можно выполнять все применимые операции
(42+0j)
~~~

При этом кватернионов, октонионов и прочих гиперкомплексных чисел там нет.

### Списки

Они еще называются массивами (пустые строки добавлены для удобства восприятия).

~~~python
>>> [1,2,3]             # список создается перечислением элементов через запятую в квадратных скобках
[1,2,3]

>>> [5,7,13] + [1,2,3]  # их можно "складывать" (объединять)
[5, 7, 13, 1, 2, 3]

>>> [1,2,3] * 3         # и даже "умножать"
[1, 2, 3, 1, 2, 3, 1, 2, 3]

>>> [1,2,3] - [1,2]     # но нельзя вычитать и делить
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for -: 'list' and 'list'

>>> [1,[2,4,6],3]       # списки могут содержать в себе другие списки
[1, [2, 4, 6], 3]

>>> [1,[2,4,6],3][1][0] # к отдельным элементам можно получить доступ при помощи индексов (отсчет ведется с 0!)
2

>>> [1,2,3,5][1:3]      # срез это список из элементов с "первого" по "третий" (помните по "нулевой" элемент?)
[2, 3]

>>> [1,2,3,5][1:]       # можно получить срез с "первого" и до конца
[2, 3, 5]

>>> [1,2,3,5][:3]       # или "сначала" и до "третьего"
[1, 2, 3]

>>> [1,2,3,5][:]        # это не имеет смысла, но тоже работает
[1, 2, 3, 5]
~~~

### Строки

Сумбурность, при которой мы от сложных структур переходим к базовым типам, кажущаяся. Теперь, зная о списках, достаточно сказать, что строка это список символов.

~~~python
>>> "Hello, Python!"  # строка это символы в кавычках (неважно, одиночных или двойных)
'Hello, Python!'
>>> "ha"+'ha'         # строки так же можно складывать
'haha'
>>> "ha"*3            # умножать
'hahaha'
>>> 'ha'[1]           # получать доступ к отдельным символам
'a'
>>> "Hello, Python!"[7:13] # или целым срезам
'Python'
~~~

Везде, где нужен список - строка может использоваться как список символов.

### Словари

Они же "ассоциативные массивы".

~~~python
>>> {'red' : 'apple', 'blue' : 'sky', 'auto' : {'brand' : 'audi', 'color' : 'white'}, 0 : 'zero'}
{'red': 'apple', 'blue': 'sky', 'auto': {'brand': 'audi', 'color': 'white'}, 0: 'zero'}

>>> {'auto' : {'brand' : 'audi', 'color' : 'white'}}['auto']
{'brand': 'audi', 'color': 'white'}

>>> {'auto' : {'brand' : 'audi', 'color' : 'white'}}['auto']['color']
'white'

>>> {'blue' : 'sky', 0 : 'zero'}[0]
'zero'
~~~

Они похожи на списки, за исключением того, что невозможно получать срезы из массива, где индексом может быть все, что угодно.

Кстати, словари и списки легко комбинируются.

~~~python
>>> {'car':['Audi','Volvo','BMV'],'plane':['Boeing','Airbus']}['plane'][0]
'Boeing'
~~~

### Множества

~~~python
>>> {0,"one",2,2,2,3}      # множество содержит уникальные значения, поэтому повторные значения не имеют смысла
{0, 2, 3, 'one'}

>>> {"one",1} | {"two",2}  # для объединения множества используется логическая операция ИЛИ
{'one', 1, 2, 'two'}

>>> {"one",2,3} & {"one","two","three"}  # логическая операция И закономерно возвращает пересечение множеств
{'one'}

>>> {"one",1,3} - {1,2}    # если вычесть из множества другое множество, исчезнут общие элементы
{'one', 3}

>>> {"one",1} + {"two",2}  # а вот складывать их почему-то нельзя
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'set' and 'set'

~~~

### Системы счисления

Программистам не надо объяснять, зачем нужны двоичная, восьмеричная и шестнадцатеричная системы счисления. 

~~~python
>>> 0b101010    # ответ на Главный вопрос Жизни, Вселенной и вообще в двоичной системе счисления (binary)
42
>>> 0x2a        # в шестнадцатеричной; `h` значит `hexadecimal`
42
>>> 0o52        # в восьмеричной; `o` значит `octal`
42
~~~