---
title: Преобразование DataView в DataTable
author: dotnetcoding
type: post
date: 2013-01-25T11:49:04+00:00
url: /coding/preobrazovanie-dataview-v-datatable.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
В .NET 2.0 появилось заметное усовершенствование: в класс DataView добавлен метод ТоТаЫе, который позволяет легко создать новый DataTable из строк, доступных в DataView. Это очень удобно при выборке множества строк из DataTable в виде нового меньшего объекта Datalanle. Его использование не должно вызвать затруднений:
  
<!--more-->


  
C#

> DataTable cust^rodTable = DataSetFiller. ’&#8217;i.llDazaset {dataFilePath) .Tables (2); DataView view &#8212; new DataView; c:us LProdTabieJ;
> 
> &#8216;Xita&#8217;i&#8217;able subsetTable &#8212; v.e«.ТоТаЫе [?<' DalaTable bubserTasle - vi ew ЛoTable '"TableKarre" ] ;

VB.NET

> Dim custP-odTable As DataIc.Dle = _
> 
> DatabetFiiler.FillDatabot(aalat&#8217;ilePath) .Tables (2)
> 
> Dim view as DataView &#8212; New DataView(custProdlable) view.Row&#8217;F&#8217;.i )tpr &#8212; &#171;ProductID > 2&#8243;
> 
> Din subsetTable as DataTable = v_ew.ToTable {)
> 
> Dur. sibssz.Tdble as DataTable = vien&#8217;.-OTable {&#171;TableNarae&#187;)

Любой из этих способов создает объект DataTabl е с тем же количеством столбцов. что и в исходном Dal aTable. Однако имеется другой перегруженный вариант, позволяющий ограничить количество столбцов, которые возвращаются в наборе результатов.

Этот метод очень полезен для поиска отдельных наборов данных — аналогично ключевому славу DISTINCT в SQL. Например, если нужно найти отдельные ProductID в таблице CustomerProducts, то эго можно легко сделать с помощью следующего фрагмента кода (обратите внимание, что первый параметр метода ToTable указывает, что результирующий DataTable должен содержать отдельные строки):

C#

> DaraTab;e custProd&#8217;Iable &#8212; DataSctFiller .FillDataset (dacaFi 1 eParh) .Tab! es (2); DataView view = qew DataV.iewl ci;stProdTable] ; view.Sown iter &#8212; &#171;ProductID > 2&#8243;;
> 
> DataTable subsetTable = vis».ToTable [true,&#187;?roductID&#187; ;;

VB.NET

> Dirr custProd&#8217;Iable As DataTabl» =
> 
> DataSetFiller.FillDataset(datsFilctatl )-Tables(2)
> 
> Dim view as DataView = ’New DataView(cjstPrcaTaale) view.Sowril-.er = &#171;ProductID > 2&#8243;
> 
> Jin subsetTable as DataTable &#8212; view.To&#8217;J’sbie(True,&#187;ProductID&#187;)

Конечно, как видите, можно применить и перегруженный вариант, если нужно извлечь DataTable с количеством столбцов, меньшим, чем в исходном объекте. Это можно сделать, указав в первом параметре false, что означает, что отдельные строки не запрашиваются:

С#

> DataTable custProdTable &#8212; DataSott&#8217;iller .FillDataser (dataFilePath) .Tables (2); DataView view = new DataView[custProdTable]; view.RowFilter &#8212; &#171;ProductlD > 2
> 
> DataTable subsetlable = vicw.ToTasle [false, &#171;CustoreerlD&#187;, &#171;ProductlD&#187;]; VB.NET
> 
> Dim custProdTable As DataTable =
> 
> DataSetFiller.FillDataset(dataFilePath).Tables(2)
> 
> Dim view as DataView &#8212; New DataView(custProdTable) view.RowFilter = &#171;ProductlD > 2&#8243;
> 
> Dim subsetTable as Dar.a’Iable &#8212;
> 
> view.ToSable(False, &#171;CustomerlD&#187;, &#171;ProductlD&#187;)

В сфере применения компьютеров повсеместно принят язык обмена данными, который используется в большинстве платформ и языков программирования — XML. Его также называют “lingua franca” компьютерного мира. Как уже было показано в предыдущих главах, автономные объекты данных, а именно объекты DataSet и DataTabl е, обеспечивают легкую работу с XML.