---
title: Поиск строки
author: dotnetcoding
type: post
date: 2012-12-25T11:32:14+00:00
url: /coding/poisk-stroki.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Часто в типичной логике программирования приложения необходимо выполнить запрос к базе данных и выбрать данные по конкретному идентификатору или первичному ключу — например, получить подробную информацию по конкретному клиенту. Этот процесс называется поиском строки. <!--more-->В случае базы данных просто выполняется SQL-запрос, но DataTable — это не таблица базы данных, и для выполнения этого действия невозможно использовать SQL-запрос и движок СУБД.

Однако класс DataTable. Rows или DataRowCollection предоставляет для этой цели метод find. При применении метода bind важно помнить, что он позволяет находить строки, работая только со столбцом, содержащим значения первичного ключа. Поэтому в базовом (не строго типизированном) объекте DataTable перед вызовом метода Find нужно либо загрузить схему, либо вручную указать в гсоде первичный ключ. 

**Использование метода Find для поиска ОДНОГО DataRow с помощью базового DataTable** 
  
на C#

> // Базовый DataTable
> 
> DataTable myTable &#8212; DataSetFj Her-FillDataset(dataFilePath)-Tables[0] ; I / Указание первичного ключа
> 
> myTable.PrimaryKey &#8212; new DataColumn [] { mylabie.Columns[&#171;CustomerlD&#187;] ]; DataRow dr = myTable.Rows.Find(&#171;2&#8243;) ;
> 
> if (dr !=> null)
> 
> {
> 
> Console.WriteLine(&#171;Поиск строки с помощью базового DataSet&#187;); ShowDataRow(dr);

**Использование метода Find для поиска одного DataRow с помощью базового DataTable на Visual Basic .NET**

> Базовый DataTable
> 
> Dim тутable As DataTable = DataSetFi,!] er.FillDataset(dataFilePath)-Tables (0)
> 
> 1 Указание первичного ключа
> 
> myTable.PrimaryKey = New DataColumn()
> 
> {myTable.Columns(&#171;CustomerlD&#187;)}
> 
> Dim dr As DataRow = myTable.Rows.FindC’2&#8243;)
> 
> If dr IsNot Nothing Then
> 
> Console .VinteLine (&#171;Поиск строки с помощью базового DataSet”)
> 
> ShowDataRow(dr >
> 
> End If 

А когда строка Найдена, можно просмотреть ее содержимое с помощью кода
  
**Вывод содержимого одной строки**
  
на C#

> > static void ShowDataRow(DataRow dr)
> > 
> > {
> > 
> > foreach (DataColumn dc m dr.Table.columns)
> > 
> > {
> > 
> > Console .Write (dr [dc] + &#187; ’’);
> > 
> > }
> > 
> > Console.Write(&#171;\n\n&#187;);
> > 
> > )
> 
> Вывод содержимого одной строки на Visual Basic .NET
> 
> > Sub ShowDataRow(ByVal dr As DataRow)
> > 
> > For Each dc As DataColumn In dr. Tacle .Columns Console.Write(dr(dc) &#038; &#187; &#171;)
> > 
> > Next
> > 
> > Console.WriteLine (&#171;&#187;)
> > 
> > End Sub
> 
> Но строго типизированные DataSet существенно облегчают эту задачу. Они предоставляют более легкий способ не только доступа к значениям отдельных столбцов для найденной строки. Но и поиска строки с использованием знакомого способа, который задействует первичный ключ. В нашем случае рассматриваелшй метод называется FindByC.ustomerlD, из названия которого понятно, что это метод Find, выполняющий поиск по столбцу CustumerlD. И более того, вместо указания объекта в качестве параметра метода Find можно просто указать Int 32