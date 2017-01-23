---
title: Коллекция Relations
author: dotnetcoding
type: post
date: 2012-07-25T10:47:19+00:00
url: /coding/kollektsiya-relations.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Свойство DataSet-. .Relations является экземпляром класса OataRel ation-Collection. Оно содержит объекты DataRelation, предназначенные для создания родительских отношений между объектами DataTable в DataSet. Примером такого типа отношения может быть соответствие первичный ключ / внешний ключ.
  
<!--more-->


  
Отношение между двумя таблицами в DataSet можно создать, вызвав метод DataSet.Relations.Add (). Имеются семь вариантов перегрузки метода Add ():

• Add(DataRelation) — добавляет в коллекцию указанный объект Data-Relation.

• Add (DataColumn, DataColumn) —создает в коллекции объект DataRelation на основе двух объектов DataCblumn. Первый аргумент содержит родительский столбец, а второй — дочерний столбец. Созданному объекту DataRelation присваивается стандартное имя.

• VB.NET. Add (DataColumn () , DataColumn () ) или С#: Add (DataColumn [ 1 . DataColumn Г]) — создает в коллекции объект DataRelation на основе двух массивов DataColumn. Первый аргумент содержит массив родительских столбцов, а второй — массив дочерних столбцов. Созданному объекту DataRelation присваивается имя но умолчанию.

• Add (String, DataColumn, DataColumn) As DataRelation — создает в коллекции объект DataRelation и заносит в свойство DataRelation. Relation-Name указанную строку.

• VB.NET. Add (String, DataColumn () , DataColumn () ) или С#: Add (String, DataColumn [ ] , DataColumn [ ] ) — создает в коллекции объект DataRelation и заносит в свойство DataRelation.RelationName указанную строку.

• Add (String, DataColumn, DataColumn, Boolean) —создает в коллекции объект DataRelation и заносит в свойство DataRelat юп. RelationName указанную строку. Объект DataRelation основан на двух столбцах DataColumn. Логический аргумент указывает, создавать ли ограничения {по умолчанию равен true).

• VB.NET. Add (String, DataColumn () , DataColumn О , Boolean) или С#: Add (String, DataColumn[], DataColumn[], Boolean) —создает в коллекции объект DataRelation и заносит в свойство DataRelation .RelationName указавную строку. Объект DataRelation основан на двух столбцах DataColumn. Логический аргумент указывает, нужно ли создавать ограничения.

Отношение в DataSet можно создавать любым из этих перегруженных методов. Вот пример применения перегруженного метода, который принимает имя отношения и два объекта DataColumn, образующих это отношение:

> C#
> 
> // Создание отношения между таблицами Customers and Orders.
> 
> myDataSet.Relations.Add(&#171;CustomersToOrders&#187;,
> 
> myDataSet.Tables[&#171;Customers&#187;].Columns(&#171;CustomerlD&#187;], myDataSet.Tables[&#171;Orders&#187;].Columns[&#171;CustomerlD&#187;]);
  
> VB.NET
  
> &#8216; Создание отношения между таблицами Customers and Orders. myDataSet.Relations.Add(&#171;CustomersToOrders&#187;, _ myDataSet.Tables(&#171;Customers&#187;).Columns(&#171;CustomerID&#187;), myDataSet.Tables(&#171;Orders”).Columns(&#171;CustomerlD&#187;)) 

В этом коде вызывается метод Add () объекта my DataSet. Relations, чтобы создать новый объект DataRelation в коллекции myDataSet .Relations. В результате в таблицу Customers добавляется новое ограничение UniqueConstraint. а в таблицу Orders добавляется ForeignKeyConstraint. Первое из них (UniqueConstraint) гарантирует уникальность в пределах таблицы всех значений родительского столбца, а второе {ForeignKeyConstramt) гарантирует, что неверное значение CustomerlD не попадет в таблицу Oraers. По умолчанию устанавливаются также каскадные удаления и обновления записей из таблицы Customers в таблицу Orders.

Можно также создать объект DataRelation явно, а затем добавить его в коллекцию Relations. Это выполняется с помощью перегруженного метода, который непосредственно принимает объект DataRelation, как показано в приведенном ниже коде:

C#

> // Создание двух объектов DataColumn DataColumn parentColumn ;
> 
> DataColumn childColumn ;
> 
> //Занесение двух столбцов в экземпляры родительского и дочернего столбца parentColumn &#8212; myDataSet.Tables[&#171;Customers&#187;J.Columns[&#171;CustomerlD&#187;] ; childColumn = myDataSet.Tables[&#171;Orders&#187;].columns[&#171;CustomerlD&#187;] ;
> 
> // Создание нового объекта DataRelation
> 
> DataRelation CustomersToOrders = New DataRelation(&#171;CustomersToOraers’&#8217;, parentColumn, childColumn) ;
> 
> // Добавление DataRelation в коллекцию DataSet.Relations myDataSet.Relations.Add(CustomersToOrders) ; 

VB.NET

> &#8216; Создание двух объектов DataColumn Dim parentColumn As DataColumn Dim childColumn As DataColumn
> 
> &#8216; Занесение двух столбцов в экземпляры родительского и дочернего столбца parentColumn = myDataSet.Tables(&#171;Customers&#187;).columns(&#171;CustometrlD&#187;) childColumn &#8212; myDataSet.Tables(&#171;Orders&#187;).Columns(&#171;CustomerlD&#187;)
> 
> &#8216; Создание нового объекта DataRelation Dim CustomersToOrders As New DataRelation(
> 
> &#171;CustomersToOrders&#187;, parentColumn, childColumn)
> 
> &#8216; Добавление DataRelation в коллекцию DataSet.Relations myDataSet.Relations.Add(CustomersToOrders)
  
> Кроме того, как уже было сказано в описании перегруженных методов, объект DataRelation можно создать на основе массива объектов DataColumn как родительских, так и дочерних столбцов. Например, представьте себе, что имеется таблица согрудников (Employees) и таблица руководителей (Managers). Таблица Managers содержит данные о сотрудниках, которые являются еще и руководителями (то есть имена таких сотрудников присутствуют и в таблице Employees, и в таблице Managers): 

C#

> // Создание массивов DataColunn для соответствующих столбцов DataColumnU parentArray = new DataColumn[2];
> 
> parentArray[0] = myDataSet.Tables[&#171;Employees&#187;].Columns[&#171;FirstNane&#187;]; parentArray[1] &#8212; myDataSet.Tables[&#171;Employees&#187;;.Columns;&#187;LastName&#187;];
> 
> DataCclurrn [ ] childArray &#8212; new DataColumn[2];
> 
> cmloArray[03 = myDataSet.Tables[&#171;Managers&#187;].columns[&#171;FirstName&#187;]; cmldArray[lj = rryDataSet.Tables [&#187;Managers&#187;] .Columns [&#171;LastName&#187;;;
> 
> DataRelation empToMngr = New DataRelation(&#171;EmployeesToManager&#038;&#187;, parentArray, childArray) ; rryDataSet.Relations.Add(EmpToMngr);

VB.NET

> &#8216; Создание массивов DataColurrn кля соответствующих столбцов Dim parentArray (2) As DataColumn
> 
> parentArray (0) &#8212; myDataSet. Tables (&#171;Employees’&#8217;} . Columns (&#171;E ucstKarre&#187;) parentArray (1) = myDataSet. Tables (&#187;Employees&#187; ) .Columns (&#187;LastName&#187;)
> 
> Dim childArray(2) As DataColumn
> 
> childArray{0) = myDataSet.Tables(&#171;Managers&#187;).Columns(&#171;FirstName&#187;) childArray(l) = myDataSet.Tables(&#171;Managers&#187;).Columns (&#171;LastNarre&#187;)
> 
> Dim empToMngr As New DataRelation!
> 
> &#171;EmployeesToManagers&#187;, parentArray, childArray) myDataSet.Relations.Add(EmpToMngr)

Здесь объект DataRelation создается с помощью массива объектов DataColumn для столбцов с первичным ключом и столбцов с внешним ключом, задающих отношения. После создания отношения в таблицу Employees заносится ограничение UniqueConstraint. обеспечивающее уникальность сочетания имени и фамилии, а в таблицу Managers заносится ограничение ForeignKeyConstraint. обеспечивающее выполнение каскадных удалений и обновлений в соответствии с отношением. Поскольку добавление UniqueConstraint выполняется при добавлении DataRelation. важно помнить, что если значения в столбце первичных ключей не уникальны, то добавление DataRelation не завершится успешно. Вместо этого будет возбуждено исключение.