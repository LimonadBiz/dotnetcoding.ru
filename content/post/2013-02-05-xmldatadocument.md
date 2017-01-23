---
title: XmlDataDocument
author: dotnetcoding
type: post
date: 2013-02-05T11:53:01+00:00
url: /coding/xmldatadocument.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Итак, с одной стороны у нас есть объект DataSet, который можно легко конвертировать в XML, а с другой стороны имеется объект XmlDocument, который может хранить XML. а при условии правильного форматирования его легко импортировать в DataSet Так что зачастую у вас будут появляться два совершенно несвязанных объекта, не имеющих ничего общего между ними. Потребуется дублировать все данные, а это чревато рассинхронизацией, которая рано или поздно все равно произойдет.<!--more-->

Но имеется объект, который может хранить и DataSet, и его XML-представление, и синхронизировать их — это объект Xml DaLaDocuroent. Он может хранить данные и выдавать их при необходимости как в виде XirlDocument, так и в виде DataSet.

Рассмотрим работу XmlDataDocument на примере:

1. Вначале создайте Windows-приложение. Назовите его Exercise 8.9 и измените текст заголовка в главной форме приложения на &#171;Exercise 8.9&#8243;.

2. Поместите на форму элемент DataGndView и назовите его dgView. Он будет выводить содержимое таблицы Customers (в объекте DataTable).

3. Поместите на форму элемент WebBrowser и назовите его xmlViewer. Он будет выводить данные из XML-документа, представленного объектом XmlDataDocument Вся форма в режиме конструирования должна выглядеть так.

4. Добавьте в обработчик события Forml_Load следующий код:

C#

> private void Forml_loaa(cbDect sender, EvertA:gt> e)
> 
> {
> 
> CustomecsTable =
> 
> CreateDataSet.DataSecFiller.F: UDataset (dataFilePath) .Tables [&#171;Customers” ] ; xdd = new XmlDataDocument(CustomersTable. DataSet) ;
> 
> dgView.DataSource = CustomersTable; xdd.Save (Application.ExecutablePai-h + &#171;\_xdd.xml&#187;); xmlViewer.Navigate(Application.ExecutablePath + &#187; xdd.xml’’); CustomecsTable.RowChanged ь= new DataRowChangeEventHandler(CustomersTable\_RowChanged);

VB.NET

> Private Sub Forml Load(
> 
> ByVal sender As System.Object, ByVal e As System.EventArgs) _
> 
> Handles MyBase.Load CustomersTable =
> 
> CreataDataSet .DataSetFiller. FillDataset (dataFilePath) .Tables (’•Customers&#187;) xdd = New XmiDataDocument(CustomersTable.DataSet)
> 
> dgViev;.DataSource = CustomersTable
> 
> xdd.Save(Application,ExecutablePatn &#038; &#171;_xda.xml&#187;)
> 
> xmlViewer.Navigate(Application.ExecutablePath &#038; &#187; xdd.xml&#187;)
> 
> End Sub 

Как видите, этот код создает новый экземпляр XmiDataDocument с именем xdd с помощью следующей строки кода:

C#

> xdd = new XmiDataDocument (CustonieirsTable. DataSet) ;

VB.NET

> xdc. == New XmiDataDocument(CustoroersTacle.DataSet)

Кроме того, он использует событие CustomersTable.RowChanged — как механизм работы с изменениями, выполняемыми с данными, которые хранятся в объекте CustomersTable. Но в случае VB.NET используется явное указание с помощью ключевого слова WithEvents, которое применяется в объявление таблицы CustomersTable:

> Private W:thl‘‘vents Сjstomers-&#8216;able As DataTacle 

В данном примере используется также простая привязка по данным, чтобы выводить данные из таблицы CustomersTable типа DataTable, а также элемент WebBrowser дли вывода результатов из объекта XmiDataDocument в виде XML.

5. В обработчике события CustomersTable .RowChanged добавьте следующий код обновления содержимого xmlViewer:

C#

> void CustomersTable_RowChanged (object sender, DataRowChangeEventArgs e)
> 
> (
> 
> xdd. Save (Application. FlxecutablePatb i &#171;\xdd.xrrl&#187;); xmlViewer,Navigate(Application.ExecutablePath + &#171;\xdd.xml&#187;);
> 
> } 

VB.NET

> Private Sub CustcrcersTafcle\_RowChanged ( \_
> 
> ByVal sender As Object, ByVal e As System.Data.DataRowChangeEventArgs) _ Handles CustomersTable.RowChanged
> 
> xdd.Save(Application.ExecutablePath £ &#171;_xda.xml&#187;)
> 
> xmlViewer.Navigate(Application,ExecutablePath &#038; &#171;_xad.xml&#187;)
> 
> End Sub

6. Откомпилируйте и запустите приложение.

7. Теперь внесите в DataTable какие-нибудь изменения. Например, измените имя Bill на Chill: вы увидите, что XmiDataDocument автоматически реагирует на это изменение, и без всяких дополнительных усилий результирующий XML соответствует содержимому DataTable.
  
Кроме того, для выполнения запросов к данным из DataSet можно использовать стандартные возможности XML вроде XPath-запросов.

BcaMOMADO.NET есть много других возможностей, связанных с XML. Некоторые из этих возможностей относятся к новому типу данных XML, введенному в Microsoft SQL Server 2005, а также есть функции наподобие ExecuceXmlReader для поставщика данных SqlClient. И, наконец, в классе System. Data. Sql Xml имеется поставщик данных, который в основном применяется для использования XML-возможностей, доступных в СУБД Microsoft SQL Server.