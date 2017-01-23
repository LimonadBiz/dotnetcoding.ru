---
title: Запросы данных пользовательских типов с помощью SQL
author: dotnetcoding
type: post
date: 2012-07-25T10:35:12+00:00
url: /coding/zaprosy-danny-h-pol-zovatel-skih-tipov-s-pomoshh-yu-sql.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Выполнять запросы к столбцу пользовательского типа можно с помощью простого оператора SQL:
  
<!--more-->


  
SELECT TESTCOLUMN FROM MYTEST

При выполнении этого оператора в SQL Server Management Studio может появиться такое сообщение об ошибке:

> An error occurred while executing batch. Error message -s:
> 
> Could not load type
> 
> &#8216;System.Data.Sql.SqlUserDefmedTypeAttribute&#8217; from assembly
> 
> &#8216;System.Data, Version=2.0 .0 .0, Culture-neutral,
> 
> PublicKeyToken=b77a5c561934e089&#8242;.

При выполнении пакета возникла ошибка. Сообщение об ошибке:

невозможно загрузить тип &#8216;. .. &#8216; из сборку; &#8216;. . . &#8216;.

Это сообщение возникает потому, что SQL Server Management Studio похоже на любое другое приложение .NET. Оно выполняет запрос к базе данных с помощью ADO.NET, а когда не может найти реализацию класса .NET для представления объекта, оно возбуждает исключение.

Обойти эту проблему можно, поместив UDT либо в GAC (Global Assembly Cache — глобальный кэш сборок), либо в один каталог с SQL Server Management Studio.

Пожалуй, легче предположить наличие ToString (), т.к. все классы в .NET является потомками System. Object, к которому имеет доступ SQL Server Management Studio.

Поэтому запрос можно записать в виде

SELECT TESTCOLOMN.ToString () FROM MYTEST но если в UDT реализованы какие-нибудь пользовательские методы, то нужен доступ к сборке, реализующей UDT.

Теперь у нас есть возможность хранения объектов в виде объектов базы данных, и можно возвратиться к обсуждению выборки данных в подключенном стиле и посмотреть, как можно выбирать пользовательские типы с помощью компонента чтения данных.