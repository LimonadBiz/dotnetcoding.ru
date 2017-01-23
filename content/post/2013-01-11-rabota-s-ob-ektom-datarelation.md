---
title: Работа с объектом DataRelation
author: dotnetcoding
type: post
date: 2013-01-11T11:41:04+00:00
url: /coding/rabota-s-ob-ektom-datarelation.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Базы данных позволяют выполнять SQL-запросы к совокупностям таблиц. Объект DataSet позволяет определить в объектах DataRelation отношение между различными таблицами, но не позволяет задавать объединения различных DataTable с помощью синтаксиса, похожего на SQL-залросы. Однако он позволяет использовать заданные DataRelation. чтобы находить дочерние строки для текущих родительских строк или родительскую строку для заданной дочерней строки.<!--more-->

Для структуры базы данных, которая использовалась в данной главе, одной из наиболее вероятных задач может быть такая: &#171;Какие клиенты заказали какие товары?&#187; В базе данных это можно выполнить с помощью оператора JOIN, но что если такое действе нужно выполнить в DataSet, где невозможно применять SQL и все возможности СУБД?

В смысле отношений такое отображение можно выполнить с помощью отношения &#171;многие ко многим&#187; в DataSet, и именно это делает строго типизированный DataSet. Вернитесь к рис. 8.1: там между таблицами Customers и Products имеется еще одна таблица CustomerProducts, которая с помощью отношения “многие ко многим&#187; позволяет выполнить отображение “многие ко миогим“.

Так что если для данного значения CustomerlD требуется найти все продукты, заказанные этим клиентом, то нужно выполнить следующие два шага:

1. Найти в таблице CustomerlD дочерние строки для данного CustomerlD.

2. Для каждой из этих дочерних строк найти соответствующие родительские строки в таблице Products.

Рассмотрим все это на примере:

1. Создайте новое Windows-приложение и назовите его Exercise 8.7. Измените текст заголовка главной формы этого приложения на “Exercise 8.7&#8243;.

2. Поместите на эту форму три списка, в которых будут отображаться строки из каждой из трех таблиц. Назовите их lbCustomers. lbCustomerProducts и lbProducts. Кроме того, создайте две кнопки, которые будут выполнять два приведенных выше тага фильтраций строк. Назовите эти кнопки btnFi iter 1
  
и btnFilter2. Измените текст на них соответственно на GetChildRows » и GetParentRow ».
  
3. В обработчик события Forml_Load вставьте следующий код:

C#

> private void Forml_Load(ob]ect sender, EventArgs e)
> 
> customerProducts &#8212;
> 
> CreateDa&#8217;.aSet.DataSetFiller.FillStrongDataSet(dataFilePath); foreach (DataRow ar in customerProducts.Tables[&#171;Customers&#187;].Rows)
> 
> {
> 
> ibCustomeri.Itenu.Add(
> 
> dr[&#171;Custorerlt;-1 ] +• * dr[&#171;FlrstNane•&#8217;] dr[&#171;LastName”]) ;
> 
> ] 

VB.NET

> Private Sub rornl_[,oad(
> 
> ByVal sender As System.Object, ByVal e As System.EventArgs) _
> 
> Handles MyBase.Load customerProcucts =_
> 
> Cr~ar.eDa&#8217;-aSet. DataSet Filler. Fill StrongDataSet (dataFilePath)
> 
> For Each dr DataRow In customerProducts.Tables(&#171;Customers&#187;).Rows laCustomers.Items.Add( _ dr (&#171;CustomerlD&#187;) &#038; &#187; : &#038; dr(&#171;FirstName&#187;) &#038; &#187; &#187; &#038; dr (&#8216;•LastName1&#8242;))
> 
> Next
> 
> Ena Sub 

Этот код, как обычно, загружает DataSet с именем customerProducts. Обратите внимание, что здесь снова используется метод Fill StrongDataSet — потому что это удобный способ получить объект DataSet с уже установленными отношениями. Если не определить отношения DataSet, их можно
  
легко добавить с помощью фрагмента кода вроде нижеприведенного (многоточие означает нужные реальные параметры):

C#

> customerProaucts.Relations.Add(new DataRelation (&#8230;));

VB.NET

> customerProaucts.Relations.Add(new DataRelation(&#8230;))

4. Теперь, если после выбора строки в списке lbCustomers щелкнуть на кнопке btnFilterl, приложение должно найти дочерние строки и занести их в список lbCustomersProducts. Это можно сделать с помощью метода GetchildRows класса DataRow.

**Поиск дочерних строк для данной выбранной строк на C#**

> private void btnFilterl_Click (object sender, EventArgs c)
> 
> [
> 
> if (lbCusLomers.Selectedlndex < 0) [ return; ) DataRow selectedRow = customerProducts-Tables["Customers"].Rows[lbCustomers.Selectedlndex]; DataRow[] childRows = selectedRow.GetchildRows(customerProducts.Relations[1]); lbCuslomerproducts.Items.Clear (); foreach (DataRow dr in childRows) [ lbCustomerProducts.Items.Add(dr["CustomerProductID"]); [

 **Поиск дочерних строк для данной выбранной строк на Visual Basic .NET**

> Private Sub bt.nFilterl_Click (
> 
> ByVal sender As System.Object, ByVal e As System.EventArgs) _
> 
> Handles btnFilterl.Click If lbCustomers.Selectedlndex < 0 Then Return End If Dim selectedRow As DataRow = _ customerProducts.Tables("Customers"). Rows(lbCustomers.Selectedlndex) Dim childRows () As DataRow = _ selectedRow,GetchildRows{customerProducts.Relations(1)) lbCustomerProducts.Items.Clear() Dim dr As DataRow For Each dr In childRows lbCustomerProducts.Items.Add(dr("CustomerProductID")) Next End Sub