---
title: Пример аннотированного типизированного DataSet
author: dotnetcoding
type: post
date: 2012-07-25T11:02:49+00:00
url: /coding/primer-annotirovannogo-tipizirovannogo-dataset.html
robotsmeta:
  - index,follow
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:1723:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="xml" style="font-family:monospace;"><span style="color: #009900;"><span style="color: #000000; font-weight: bold;">&lt;?xml</span> <span style="color: #000066;">version</span>=<span style="color: #ff0000;">&quot;l.О&quot;</span> encoding’=<span style="color: #ff0000;">&quot;utf-8&quot;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span></span>
    &nbsp;
    <span style="color: #009900;"><span style="color: #000000; font-weight: bold;">&lt;xs:scnema</span> <span style="color: #000066;">id</span>=<span style="color: #ff0000;">&quot;3ookDataSet&quot;</span></span>
    &nbsp;
    <span style="color: #009900;"><span style="color: #000066;">targetNamespace</span>=<span style="color: #ff0000;">&quot;urn:apress-proadonet-chapter6-BookDataSet.xsd&quot;</span> <span style="color: #000066;">elementFormDefault</span>=<span style="color: #ff0000;">&quot;qualified&quot;</span> <span style="color: #000066;">xralns</span>=,<span style="color: #ff0000;">'urn:apress-proadonet-chapter6-BookDataSet.xsd&quot; xmlns:mstns=&quot;urn:apress-proadonet-chapter6-BookDataSet.xsd&quot; xmlns:xs=”http://www.w3.org/2001/XMLSchema&quot;</span></span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?xml version=&quot;l.О&quot; encoding’=&quot;utf-8&quot; ?&gt;
    
    &lt;xs:scnema id=&quot;3ookDataSet&quot;
    
    targetNamespace=&quot;urn:apress-proadonet-chapter6-BookDataSet.xsd&quot; elementFormDefault=&quot;qualified&quot; xralns=,'urn:apress-proadonet-chapter6-BookDataSet.xsd&quot; xmlns:mstns=&quot;urn:apress-proadonet-chapter6-BookDataSet.xsd&quot; xmlns:xs=”http://www.w3.org/2001/XMLSchema&quot;</p></div>
    ";}
categories:
  - .NET Программирование

---
Теперь мы уже знаем, как аннотировать DataSet р управлять генерацией его кода, чтобы иметь точный контроль над его поведением, ограничениями и правилами. А теперь рассмотрим все это в действии на одном примере. В этом примере мы создадим приложение на базе Windows-формы, которое будет называться Example 6.9. Добавьте в проект новый элемент, выберите для него тип DataSet и имя BookDataSet. xsd. Вставьте в новый XSD-файл класса DataSet следующий аннотированный XSD-код:<pre lang='xml">

<?xml version="l.О" encoding’="utf-8" ?> <xs:scnema id="3ookDataSet" targetNamespace="urn:apress-proadonet-chapter6-BookDataSet.xsd" elementFormDefault="qualified" xralns=,'urn:apress-proadonet-chapter6-BookDataSet.xsd" xmlns:mstns="urn:apress-proadonet-chapter6-BookDataSet.xsd" xmlns:xs=”http://www.w3.org/2001/XMLSchema" </pre> 

Теперь перейдем к еще не знакомому действию. Visual Studio .NET автоматически помещает объявление пространства имен msddata в ваши схемы DataSet, но чтобы получить доступ к префиксу пространства имен codegen, придется ввести кое-что вручную:

> <xmlns : codegen-=”urn: schemas-microsof t-com:xml-msprop’' xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">
> 
> <xs:element name=-”BookDataSef msdata: IsDataSet="truel,>
> 
> <xs:complexType>
> 
> <xs:choice maxOccurs="unbounded">

Вот так выглядит результат первого применения пространства имен codegen. В следующем коде указано, что свойство typedName элемента Books (что соответствует дескрипторам <Books> в экземпляре XML-документа) будет называться Book, a typedPlural будет называться Books:

> <xs:element name="Books" codegen:typedKarr.ej!"Book" codegen:typedPlural=”Books">
> 
> <xs:complexType>
> 
> <xs:sequence>
> 
> <xs:element name="BookID" type="xs:integer" minOccurs-"!" /> <xs:element name="Title" type-"xs:string" minOccurs="l" /> <xs:eiement narae="Publisher" type-"xs:string" rcinOccurs="l" />
> 
> </xs:sequence>
> 
> </xs:complexType>
> 
> </xs: elerr.ent> 

В случае дескрипторов <Books> на отдельные элементы накладываются некоторые логичные соглашения по именованию. Теперь отдельная строка таблицы будет называться BookReview, а не BookReviews:

> <xs: element name=''BookReviews'' codegen:typedName-"BookReview" codegen :typedPlural=-"BookReviews''>
> 
> <xs:complexType>
> 
> <xs:sequence? <xs:elenent name="BookID" type="xs: integer” min0ccurs=''0" /> <xs:element name="Rating" type="xs:1nteger" min0ccurs=”0" /> <xs:element name="Review'’ type=”xs:string" min0ccurs-"0" />
> 
> </xs:sequence? </xs:complex'! ype>
> 
> </xs:element>
> 
> </xs:choice>
> 
> </xs:complexType>
> 
> <xs:key name="KeyBookID">
> 
> <xs:selector xpath=".//mstns:Books" />
> 
> <xs:field xpath="mstns:BookID" />
> 
> </xs:key>

И, наконец, в XSD-файле имеется пара действительно интересных моментов. Первый момент —управляющий элемент DataGridView использует имя отношения для создания визуальной связи с дочерними таблицами. Значит, теперь нужно обеспечить, чтобы в пользовательском интерфейсе это имя выглядело достаточно прилично! Кроме того, мы переименовали функцию GetBookReviewsRows О . которая уже встречалась нам, на Reviews ():

> <xs;keyref name="Reviews” refer="KeyBookID” codegen;typedParent="Sook" codegen: typedChildren""Reviews"? <xs;selector xpath=".//mstns:BookReviews" />
> 
> <xs:field xpath-"mstns:3ookID" />
> 
> </xs:keyref>
> 
> </xs:element? </xs:schema>

Теперь перейдем к форме приложения. Измените заголовок формы (свойство Text) на “Annotated Typed DataSet Binding Example" (Пример привязки аннотированного типизированного DataSet). Это форма должна содержать два управляющих элемента: DataGridView с именем dgBooks и кнопку с именем btnSumScores и текстом Sum Scores (Просуммировать баллы). Кроме того, в форму нужно добавить приватное поле типа BookDataSet с именем Books:

> C#
> 
> private BookDataSet books;
> 
> VB.NET
> 
> Private books As BookDataSet

У нас есть конструктор события form_load, относящегося к форме, который нужно изменить так, чтобы загрузить в форму данные XML (уже знакомый нам файл Books. xml, который копируется в корневой каталог приложения):

> C#
> 
> public Forml()
> 
> {
> 
> InitializeComponent();
  
> books = new BookDataSet (); books. ReadXml ("Books .xml1’) ; datagndBooks .DataSource = books.Books;
> 
> }
> 
> VB.NET
> 
> Private Sub Forml\_Load( \_
> 
> ByVal sender As System.Object, ByVal e As System.EventArgs)
> 
> Handles MyBase.Load books = New BookDataSetО books.ReadXml("Books.xml") datagndBooks. DataSource = books. Books End Sub

Кроме того, чтобы показать, насколько незамысловат наш новый аннотированный класс, задействуем кнопку Sum Scores, чтобы она выводила сообщение с суммой всех оценок обзоров. Можно просто выполнить последовательный просмотр таблицы Reviews, но мы используем синтаксис For. . .Each, чтобы продемонстрировать, как похож синтаксис кода на словесное описание этих действий, которым мы воспользовались бы при беседе с другим программистом:

> C#
> 
> private void btnSumScores_Ciick(object sender, EventArgs e)
> 
> {
> 
> i nt sum = 0;
> 
> )
> 
> VB.NET
> 
> Private Sub btnSumScores_Click|ByVal sender As System.Object,
> 
> ByVal e As System.EventArgs) Handles btnSunScores.Click Dim sum As Integer = 0
> 
> End Sub 

Вот в этом и состоит прелесть типизированных DataSet. У нас не только есть функции доступа без (видимого) использования индексов массивов или коллекций. но и все остальное имеет подходящие имена и строго типизировано, так что при попытке использовать неверный тип данных будет возбуждено исключение. Проход по иерархии данных выполняется невероятно просто:

> C#
> 
> foreach (BookDataSet.Book book in books.Books)
> 
> {
> 
> foreach (BookDataSet.BookReview review in book.Reviews ())
> 
> {
> 
> sum +- Convert.ToInt32(review.Rating);
> 
> 1
> 
> }
> 
> MessageBox.Show (this, ''ScorG Total: " + sum. ToString ());
  
> VB.NET
  
> For Each Book as BookDataSet.Book In Books.Books
> 
> For Each review as BookDataSe-.BookReview In Book.Reviews() sum += CInt(review.Rating)
> 
> Next
> 
> MessageBox.Show(Me, "Score Total: " + sum.ToString()>

насколько лучше все выглядит, когда имеются аннотация \ имена, понятные для людей и программистов.