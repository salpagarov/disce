---
title: Совсем другая книга про Go
---

# Совсем другая книга про Go

"Маленькие книги" Карла Сегуина – лучшие в жанре "быстрого старта". В них ничего лишнего, только самое главное – подробности, в которых так легко утонуть поначалу, потом так же легко восполняются правильно заданными вопросами и самостоятельно найденными ответами. 

Когда-то "Маленькая книга про Go" вдохновила меня написать несколько других "маленьких книг" на темы, для которых книг Карла не было. А потом, когда я сам пришел к Go и вернулся к этой книге, вдруг оказалось, что демонстрационные примеры еще работают, а вот что-то реальное написать уже не получается. Как же так получилось?

Все меняется, иногда – радикально. Модули в обновленном Go настолько отличаются от прежних, что написать что-то сложнее HelloWorld стало почти невозможно. Но, начав однажды писать, я не смог остановится и решил во всем этом разобраться и записать. Подробные записи всегда делаются для себя, но я надеюсь, пользу они принесут не только мне.  Это будет совсем другая книга про Go. Не судите строго.

В двух словах – Go это “C++ для маленьких”. Звучит странно, но именно такие ожидания были в Google для нового языка программирования – простой, производительный и безопасный. В итоге получился компактный компилируемый язык со строгой типизацией, автоматическим управлением памятью, встроенной поддержкой многозадачности и модульной организацией кода со своим менеджером пакетов. 

Язык хорош во всем, кроме кривой обучения. В качестве первого языка он не то, чтобы ужасен -- но с самого начала нужно знать то, что обычно изучается чуть ли не последним. Рассказывать о нем -- настоящий вызов. Но я попробую. Опять же, не судите строго.

## Команда Go

Это официальное название. Одна-единственная "команда go" используется для компиляции, выполнения, тестирования, управления зависимостями, форматирования исходного кода… для всего.  Настоящий "швейцарский нож", осваивать который лучше постепенно.

## Первая программа

Пройти все этапы от написания кода до его выполнения – первый урок в изучении любого языка программирования.

В любом текстовом редакторе создайте файл `hello.go`:

~~~go
package main
import "fmt"

func main() {
    fmt.Println("Hello, world!")
}
~~~

Выполните его:

~~~
$ go run hello.go
Hello, world!
~~~

Или скомпилируйте и выполните:

~~~
$ go build hello.go
$ ./hello
Hello, world!
~~~

В результате мы получим двоичный исполняемый файл для вашей операционной системы (Windows, Linux, MacOS, Android, iOS и еще много других) и вашего процессора (тоже с десяток разновидностей). Причем, из любого сочетания вы можете компилировать под любые другие.

## Модули

Программа на Go состоит из модулей. Одни входят в стандартную библиотеку, другие ваши собственные, третьи написаны кем-то еще. Одним модулям для работы нужны другие, а тем какие-то еще и все это в конечном итоге образует дерево зависимостей. Все эти модули компилируются в исполнимый файл, если на вершине этого дерева находится модуль `main`, или в еще один "кубик" для других программ -- если у модуля на вершине другое название.

В нашей первой программе мы как раз и создали модуль `main` (строка `package main`). Для работы ему нужен модуль `fmt` для того, чтобы вывести на экран строку в нужном формате (строка `import "fmt"`). Все это выполняется в функции `main`.  В программе на Go выполнение начинается с функции `main` модуля `main`.

> Такие сущности называются "магическими", потому что особые свойства им придают их особые имена.

## Функции





---







## Декомпозиция

Можно написать программу полностью, от начала до конца. Но зачем, если некоторые задачи уже решены и мы можем просто этим воспользоваться? К примеру, в нашей первой программе мы выводим приветственное сообщение, не особенно вникая, как это происходит. `Println` выводит нужную строку на экран, избавляя нас от необходимости разбираться, какие системные вызовы для этого использовать, как операционная система взаимодействует с драйверами и как драйверы формируют на экране монитора нужное изображение. И так во всем, стандартная библиотека содержит много всего, что позволяет нам не отвлекаться на мелочи.

Это и есть декомпозиция – разделение задачи на подзадачи, некоторые их которых уже могут быть решены. 

## Модули

Функции произвольно (на самом деле тематически) сгруппированы по модулям, которые являются вторым элементов декомпозиции. В Go все состоит из модулей. Одни из них входят в стандартную библиотеку, другие – ваши собственные, третьи написаны кем-то еще. 







## Декомпозиция

Это и есть декомпозиция – разбиение задачи на более простые, часть из которых уже решены. Функции являются одним из двух элементов декомпозиции. Они так называются из-за того, что получают на вход аргументы и возвращают результат, хотя в отличие от математических функций могут не только вычислять возвращаемое значение, но и делать какие-то другие действия. 



## Модули

Любая программа на Go состоит из модулей. Модуль это основая (точнее, единственная) единица декомпозиции. А декомпозиция, как мы знаем, это способ разделения на части.



 Одним модулям для работы нужны другие модули, им, в свою очередь, нужны еще какие-то и так далее. В итоге программа собирается из модулей, которые все вместе образуют дерево зависимостей, на самом верху которого находится модуль `main` с функцией `main`. Это особенный модуль и особенная функция – в собранной программе будут все модули из дерева зависимостей, но выполнение программы начнется именно с этой функции этого модуля.

> Такие сущности называются "магическими", потому что особые свойства им придают их особые имена.









Создадим директорию для нашей программы и перейдем в нее:

~~~
$ mkdir myDemoProject
$ cd myDemoProject
~~~

Затем инициализируем наш новый модуль:

~~~
$ go mod init DEMOD
~~~

Имя модуля – отсылка к вселенной комиксов Marvel. Если оно вам незнакомо – просто забейте. Важно то, что исполнимый файл после создания будет называться именно так.

В итоге будет создан файл с вот таким содержанием:

~~~
module DEMOD

go 1.24.3
~~~

1.24.3 – текущая версия Go, установленная на моем компьютере на момент написания этих строк. Она может (и, наверняка, будет) отличаться.

Скопируйте сюда нашу первую программу `helloworld.go`, затем соберите и запустите ее:

~~~
$ go build
$ ./DEMOD
Hello, world!
~~~

Все точно так же, да. Но теперь мы создали модуль DEMOD, а в нем – модуль `main`. И не просто выполнили программу, а создали исполняемый файл, который можно запустить не только здесь, где у вас установлена среда разработки, а на любом другом компьютере с такой же операционной системой, что и у вас.

> Здесь замечу, что в любой поддерживаемой операционной системе можно создать исполнимый файл для любой другой, но это тоже деталь, о которой сейчас не время говорить.

##— 

## Переменные

### Области видимости

### Время жизни

## Типы данных

### Базовые

### Композитные (составные)

### Функции

## Управление потоком

### Декомпозиция

### Ветвление

### Циклы