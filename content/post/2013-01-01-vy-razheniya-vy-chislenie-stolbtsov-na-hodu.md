---
title: 'Выражения: вычисление столбцов на ходу'
author: dotnetcoding
type: post
date: 2013-01-01T11:35:50+00:00
url: /coding/vy-razheniya-vy-chislenie-stolbtsov-na-hodu.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Иногда нужно произвести вычисления со столбцами табличного набора результатов, чтобы полученные значения выглядели как столбец этого набора. <!--more-->Вот вполне возможный реальный пример: в таблице Products (Товары) имеются столбец с ценой (Price) и столбец с величиной налога (Tax), но понадобилось создать набор результатов с еще одним столбцом, содержащим отпускную цену, которая рассчитывается по формуле Цена + Цена * ГТроцечтМалога.


  
Это легко можно сделать, послав к базе данных SQL-запрос

> Select ProductID, Price, Tax, (Price к Price ” TaxPercent] as TotalPrice from Products;

Здесь отпускная цена (TotalPrice) определятся выражением. Затем СУБД вычисляет значения TotaiFrice для всех строк и включает их в набор результатов.

Тот же результат можно получить, указав в DataTable выражение для нужного нового столбца. Чтобы нагляднее показать, что выражение вычисляется для Каждой строки DataTable, в следующем примере используется DataTable, привязанный по данным к элементу DataGridView Windows-приложения. Это можно сделать, выполнив следующие шаги:

1. Вначале создайте приложение на базе Windows-формы . Замените текст заголовка главной формы приложения на “Exercise 8.5”.

2. Поместите на форму элемент DataGndView иустановите его свойство Dock в Dock. Fill. По умолчанию ему будет присвоено имя dataGridViewl.

3. В обработчике события Forml_Lload, который вызывается при загрузке Forml, добавьте код, приведенный в листингах.

**Создание вычисляемого столбца**
   
на C#

> DataSet customerProducts =
> 
> CreateDataSet.DataSetFiller.Fills t гол gDai.aSet(dataFilePath);
> 
> DataTable productsTable = customerProducts.Tables[1];
> 
> DataColumn totalPrice &#8212; new DataColumn(&#171;Total Pr-ce&#187;); totalPrice.Expression = &#171;Price + Price * TaxPercent&#187;;
> 
> productsTable.Columns.Add(totalPrice]; dataGridViewl.DataSource &#8212; productsTable;

**Создание вычисляемого столбца на Visuai Basic .NET**

> Dim customerProducts As DataSet = _
> 
> CreateDataSet.DataSetFiller.FillStrongDataSet(dataFilePath) Dim productsTable As Da-aTable “ customerProducts.Tables(1)
> 
> Dim tocalpnce As DataColumn = New DataColumnC&#8217;Total Price&#187;) totalPrice.Expression = &#171;Price + Price * TaxPercent&#187;
> 
> productsTable.Columns.Add(totalPrice) dataGridViewl.DataSaurce = productsTable

4. Скомпилируйте и запустите приложение. Выходные данные должны быть похожи видно, что столбец TotalPnse правильно вычисляется по заданному выражению и включен в DataTable. Так что же на самом деле делает этот код?
  
Ну, прежде всего мы видим, что DataSet заполняется с помощью метода FillStrongDataSet. а не метода FillDataSet. Это очень важно, т.к. чтобы выражения работали, нужно, чтобы столбцам были присвоены типы данных. Невозможно выполнить операцию умножения для двух столбцов типа System. String, а это стандартный тип столбца для базового класса DataColumn.

Вместо этого можно указать свойство DataType для базовых объектов DataColumn; но такую операцию нужно выполнить до заполнения данными. Это можно легко сделать с помощью следующих строк кода:

> C#
> 
> productsTable.Columns[&#171;Price&#187;].DataType = typeof(System.Int32);
> 
> // Заполнение данными
> 
> VB.NET
> 
> productsTable.Columns(&#171;price&#187;).DataType «• GetType(System.Int32)

Заполнение данными

Либо можно просто неявно преобразовать строго типизированный DataSet в базовый DataSet:

C#

> DataSet customerProducts =
> 
> CreateDataSet.DataSetFiller.FillStrongDataSet(dataFilePath);

VB.NET

> Dim customer.Products As DataSet =
> 
> CreateDataSet.DataSetFiller.FillStrongDataSet(dataFilePath)

Обратите внимание, что неявное приведение типа не требует выполнения каких-то действий, можно просто присвоить значение объекта-потомка назад экземпляру базового класса. При наличии готового объекта DataTable следуюгцие три строки добавляют новый столбец с именем total Price, устанавливают для него выражение и добавляют его в DataTable:

C#

> DataColumn totalPnce = new DataColumn(&#171;Total Price&#187;);
> 
> totalPrice.Expression = &#171;Price + Price * TaxPercent&#187;;
> 
> productsTable.Columns.Add(totalPricei ;

VB.NET

> Dim totalPrice As DataColumn = New DataColumn(&#171;Total Pr^ce&#187;) totalPrice.Expression = &#171;Price + Price * TaxPercent1&#8242;
> 
> productsTable.Columns.Add(totalPrice) 

Вот и все! Следующая строка просто выполняет привязку по данным объекта DataTable и компонент DataGridView, чтобы можно было вывести результаты: C#

> dataGridViewl.DataSource &#8212; productsTable;

VB.NET

> dataGridViewl.DataSource = productsTaole

Этот подход хорошо работает в тех ситуациях, когда нужно выполнять вычис ления для каждой стропи из DataTable. Но в некоторых ситуациях может иона добиться выполнить сложные вычисления по всему DataTable. К счастью, для таких случаев DataTable поддерживает метод Compute.