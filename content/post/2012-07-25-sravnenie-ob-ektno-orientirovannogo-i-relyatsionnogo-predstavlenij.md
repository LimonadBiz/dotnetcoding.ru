---
title: Сравнение объектно-ориентированного и реляционного представлений
author: dotnetcoding
type: post
date: 2012-07-25T10:31:41+00:00
url: /coding/sravnenie-ob-ektno-orientirovannogo-i-relyatsionnogo-predstavlenij.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Представьте себе, что нам нужно создать приложение работы с географическими картами. Каждая точка на карте представляется парой координат X и Y. Как хранить такую информацию в базе данных?
  
<!--more-->


  
Эту информацию можно хранить в виде двух целочисленных столбцов. Но тогда у нас не будет приемлемого способа различения коордниат при, скажем, выполнении преобразования из километров в мили с помощью справочной таблицы, данные в которой хранятся в аналогичном формате. Вообще-то любав операция, которую может потребоваться выполнить с двумя координатами, потребует чтения из базы данных лвух столбцов и занесения их в бизнес-объект или представление в виде класса XYCoOrair.ate, в котором можно реализовать основные функции, например, расстояние от начала координат (0, 0).

Ну а если понадобится выполнить SQL-запрос, чтобы определить, какая точка из данного множества точек дальше всего находится от начала координат?

Другим способом хранения таких данных может быгь столбец типа varchar, в котором хранятся координаты X и Y. но если нужно выполнять с ними какие-то действия, их все равно придется выбирать из базы данных и преобразовывать в объектное представление.

Было бы гораздо лучше, сели бы можно было взять объект и просто сохранить его в базе данных.