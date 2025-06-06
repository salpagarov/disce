---
title: Совсем другая книга про Go
---

# Совсем другая книга про Go
## Введение

"Маленькие книги" Карла Сегуина – лучшие в жанре "быстрого старта". В них только самое главное. Подробности, в которых так легко утонуть поначалу, потом, когда общая картина уже сложилась, так же легко восстанавливаются правильным вопросами и самостоятельно найденными ответами.

Когда-то "Маленькая книга про Go" вдохновила меня написать несколько других "маленьких книг" – на темы, для которых книг Карла не было. А потом, когда я сам пришел к Go и вернулся к этой книге, вдруг оказалось, что демонстрационные примеры еще работают, а вот что-то реальное написать уже не получается. Как же так вышло?

Все меняется, иногда – меняется драматически. Модули в обновленном Go настолько отличаются, что написать что-то сложнее HelloWorld становится почти невозможным. Начав однажды писать, я не смог остановиться и решил во всем этом разобраться и записать. Подробные записи всегда делаются для себя, но я надеюсь, пользу они принесут не только мне. 

Это будет совсем другая книга про Go. Не судите строго.

## Инструменты

### Команда Go

Это официальное название. Одна-единственная "команда go" используется для компиляции, выполнения, тестирования, управления зависимостями, форматирования исходного кода… вообще для всего.  Настоящий "швейцарский нож", осваивать который мы будем постепенно.

### Среда разработки

vi, nano, notepad – у каждого программиста есть свой любимый инструмент для написания исходного кода. А еще есть интегрированные среды разработки (IDE) вроде платного Goland от JetBrains или свободного VSCode от Microsoft. Выбор есть всегда, но если вы его еще не сделали, посмотрите в сторону последнего. В VSCode официальная поддержка Go очень неплоха, пройдет очень много времени до момента, когда (и если!) его возможностей станет недостаточно.

## Первая программа

Пройти все этапы от написания кода до его выполнения – первый урок в изучении любого языка программирования и проверка работоспособности установленных инструментов разработки.

В любом текстовом редакторе создайте файл `hello.go`:

~~~go
package main
import "fmt"

func main() {
    fmt.Println("Hello, world!")
}
~~~

Выполните его:

~~~bash
$ go run hello.go
Hello, world!
~~~

Или скомпилируйте и выполните:

~~~bash
$ go build hello.go
$ ./hello
Hello, world!
~~~

## Модули

*Здесь мы забежим вперед и рассмотрим модульную организацию программ на Go – сначала главное, помните?*











Любая программа на Go состоит из модулей. Одни из них входят в стандартную библиотеку, другие – ваши собственные, а третьи написаны кем-то еще. Все эти кубики зависят друг от друга и вместе образуют дерево зависимостей, где на самом верху находится модуль `main` c функцией `main`, а дальше – все модули, которые нужны для его работы и модули, которые нужны для работы им. Если модуль `main` отсутствует, то ваш код можно использовать в других программах – то есть станет для кого-то внешней библиотекой. Но построить собственную программу без модуля `main` нельзя. 

> Такие сущности называются "магическими", потому что особые свойства им придают их особые имена.

















Создадим директорию для нашей программы и перейдем в нее:

~~~
$ mkdir myDemoProject
$ cd myDemoProject
~~~

Затем инициализируем наш новый модуль:

~~~
$ go mod init SHIELD
~~~

Имя модуля – отсылка к вселенной комиксов Marvel. Если оно вам незнакомо – просто забейте. Важно то, что исполнимый файл после создания будет называться именно так.

В итоге будет создан файл с вот таким содержанием:

~~~
module SHIELD

go 1.24.3
~~~

1.24.3 – текущая версия Go, установленная на моем компьютере на момент написания этих строк. Она может (и, наверняка, будет) отличаться.

Скопируйте сюда нашу первую программу `helloworld.go`, затем соберите и запустите ее:

~~~
$ go build
$ ./SHIELD
Hello, world!
~~~

Все точно так же, да. Но теперь мы создали модуль SHIELD, а в нем – модуль `main`. И не просто выполнили программу, а создали исполняемый файл, который можно запустить не только здесь, где у вас установлена среда разработки, а на любом другом компьютере с такой же операционной системой, что и у вас.

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
