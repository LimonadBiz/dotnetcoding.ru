---
title: Выполнение агрегатных вычислений
author: dotnetcoding
type: post
date: 2013-01-05T11:38:03+00:00
url: /coding/vy-polnenie-agregatny-h-vy-chislenij.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Предположим, что нужно выполнить какие-то вычисления над строками таблицы. Пусть в нашем случае нужно добавить во все строки столбец Priсе и получить общую сумму стоимости всех продуктов.<!--more-->

Если бы мы работали с базой данных, можно было просто налисать такой за прос:

> Select Sum(Pnce) from Products

Этот запрос просмотрел бы все строки и просуммировал бы по одному их столбцы Price, а затем возвратил бы общую сумму. В классе DataTable такой же ре зультат позволяет получить метод Compute, продемонстрированный в листингах 8.15 и 8.16. В этом коде компонент btnSumPrices — это кнопка, при щелчке на которой выполняется вычисление агрегированной суммы по столбпу Price, и вычисленное значение заносится в метку IblSumPrice.

**Использование метода Compute на C#**

> private void Forml Loadiobject sender, EventArgs e)
> 
> {
> 
> DataSet customerProducts =
> 
> CreateDataSet.DataSetFiller-FillstrongDataSet(aataFilePath);
> 
> Переменная productsTable определена в классе как призагная. productsTable = customerProducts.Tablesfl;;
> 
> DataColumn totalPrice &#8212; new DataCoiumn (&#171;Total Prico&#187;); totalPrice.Expression = &#171;Price + Price * TaxPercent&#187;; productsTable.Columns.Add(totalPn ce); dataGridViewl.DataSource = productsTable;
  
> private void btnSumPrices Click(ab;ject sender, EventArgs e!
> 
> {
> 
> string price я productsTable.Compute {&#171;Sum(Price) &#187; , &#171;&#187;) .ToStringO ;
> 
> lblSumPrice.Text = &#171;The total price is : &#187; + price;
  
> Листинг 8.16. Использование метода Compute на Visual Basic .NET
> 
> Private Sub Forml Load(
> 
> ByVal sender As System.Object, ByVal e As System.EventArgs) Hardies MyBase.Iioad Dim customerProducts As DataSet = __
> 
> CreatoDataSet.DataSetFiller.FillStrongDataSet(dataFilePath) 1 Переменная productsTable определена в классе как приватная. productsTable = customerProducts.Tables (1)
> 
> Dirr totalPrice As DataColumn &#8212; Mew DataColumn(&#171;Total Price&#187;) totalPrice.Expression = &#171;Price + Price * TaxPercent&#187; productsTable.Columns.Add(totalPrice) dataGndViewl .DataSource = productsTable Erd Sub
> 
> Private Sub btnSumPnces_Click (
> 
> ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnSumPrices.Click Dim price As String = _
> 
> productsTable.Compute(&#171;Sum(Price)&#187;, &#171;.ToString{> lclSumPrice.Text = &#171;The total price is : &#187; &#038; price End Sub 

Вы можете легко модифицировать этот код, чтобы выполнить вычисления только над подмножеством строк, выбираемым по заданному условию. Например, если нужно подсчитать сумму всех стоимостей, меньших 500, то в предыдущий код можно включить следующий фрагмент:

> C#
> 
> string price =
> 
> productsTable.Compute(&#171;Sum(Price)&#187;, &#171;Price < 500").ToString 0; VB.NET Dim price as String = productsTable.Compute ("Sum(Price)", "Price < 500").ToString0;

Окончательный вид работающего приложения с фильтром для цен, меньших 500.

Кроме этого. СУБД позволяют выполнить еще одно важное действие; указать ограничение внешним ключом между множествами полей из различных таблиц. Во многих случаях можно указать в базе данных объединения, чтобы выбрать агрегированные наборы результатов из нескольких таблиц с учетом соответствующих или предполагаемых отношений. Как уже было сказано, если DataTable является находящимся в памяти аналогом табличных данных (т.е. похож на таблицу базы данных), то на отношение больше всего похожи объекты DataRelation.