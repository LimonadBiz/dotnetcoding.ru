---
title: Выборка данных пользовательских типов в подключенном стиле
author: dotnetcoding
type: post
date: 2012-07-25T10:36:06+00:00
url: /coding/vy-borka-danny-h-pol-zovatel-skih-tipov-v-podklyuchennom-stile.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Для выборки UDT из базы данных в подключенном стиле есть несколько способов. Во всех этих способах применяется объект Sql Command и объект SqlDataReader. Если UDT используются автономно с помощью адаптера данных, то объект DataAdapter неявно будет использовать компонент чтения данных.
  
<!--more-->


  
Наиболее очевидный способ сделать это — просто использовать команду с методом ToString:
  
C#

testCommand.CorrmandText &#8212; &#171;SELECT TESTCOLUMN.ToStringО FROM MYTEST&#187;;

VB.NET

testCommand.CommandText = &#171;SELECT TESTCOLUMN.ToString () FROM MYTEST&#187;

Этот метод позволяет выбирать текстовое представление UDTc помощью метода GetSring компонента чтения данных:

С #

string udtRepresenta^ion &#8212; sqiDr.GetString(O);

VB.NET

string udtRepresentation = sqlDr-GetStrmg (0)

Еще один вариант этого же кода — указание текста команды SqlCommand в внде

SELECT TESTCOLUMK FROM MYTEST и применение метода ToString () к объекту, выбранному из объекта чтения данных:

string udtRepresentaci on = sqlDr [ 0] .ToString () ;

Однако основная ценность UDT проявляется тогда, когда есть возможность выбрать данные и представить их в виде объектов, а ые строковых представлений.

Это можно легко сделать, выполнив преобразование типа выбранного объекта, как было показано выше, но вместо вызова метода ToString можно преобразовать объект в его представление:

C#

XYCoOrdinate хус = (XYCoOrdinate) sqlDr[0J;

VB.NET

Dim хус as XYCoOrdinate &#8212; CCype(sqjDr(0), XYCoOrdinate))

Теперь пользовательский тип доступен нам в внде строго типизированного объекта. и можно либо непосредственно вызывать различные методы, реализованные для этого объекта, либо преобразовать его в подходящий класс, если это позволяет сделать ваша объектная модель.