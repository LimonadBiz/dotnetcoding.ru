---
title: Создание объекта DataView
author: dotnetcoding
type: post
date: 2013-01-20T11:47:38+00:00
url: /coding/sozdanie-ob-ekta-dataview.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Объект DataView можно создать с помощью одного из трех поддерживаемых перегруженных вариантов конструктора. Первый вариант создает экземпляр DataView, но не передает ему никакой информации:
  
<!--more-->

> C#
> 
> DataView myView &#8212; new DataView () ;
> 
> VB.NET
> 
> Dim myView as DataView = New DataView() 

Второй конструктор непосредственно связывает DataView с DataTable. После создании такого DataView можно задать его другие различные свойства, чтобы создать “представление” данных из DataTable. Это делается с помошью следующего фрагмента кода:

> C#
> 
> DataView myView &#8212; new DataView(myTable) ;
> 
> VB.NET
> 
> Dim myView as DataView = New DataView(myTable)

Третий, и последний, конструктор DataView позволяет указать всю зту информацию в одной строке кода. В нем можно указать не только таблицу, но и критерии сортировки, поиска и фильтрации RowState. Для этого нужен следующий фрагмент кода:

> C#
> 
> DataView dv = new DataView (
> 
> productsTable, &#171;ProductTD = 1&#8243;, &#171;ProductName&#187;,
> 
> DacaViewRowState.Unchanged);
> 
> VB.NET
> 
> DataView av = new DataView (
> 
> productsTable, &#8216;’ProductiD = 1&#8243;, &#171;ProductName&#187;,
> 
> DataViewRowState.Unchanged)

Итак, чтобы указать всю необходимую информацию в одной строке кода, можно либо использовать третий вариант перегрузки, либо воспользоваться следующими свойствами класса DataView для передачи нужной информации:
  
* RowFilter. Это свойство позволяет задать критерий выбора, аналогично передаваемому в метод Select класса DataTable, и позволяет фильтровать возвращаемые строки. К примеру, CustomerlD &#8212; 4 возвратит для наших данных информацию о потребителе Тарзан.

* Sort. Это свойство позволяет указать порядок сортировки возвращаемых данных.

* RowStateFilter. При выполнении изменений в DataTable этот объект ведет пошаговую историю выполненных изменений. Это свойство позволяет задать значение DataViewRowState и определять версии данных.

Другие способы поиска в объектах DataRowView, содержащихся в объекте DataView — методы Find и FindRows.

* Find. Работает аналогично методу DataTable .Rows. Find, но не совпадает с ним в точности. Он позволяет указать критерий или предикат для поиска в столбцах, упомянутых в свойстве Sort объекта DataView. Sort и Find работают совместно, т.к. значение, указываемое в качестве фильтра метода Find, вычисляется только для сортируемого столбца. Можно указать одну строку, удовлетворяющую заданному критерию. Но такая строка возвращается в виде индекса строки, удовлетворяющей заданному критерию.

* FindRows. Позволяет возвратить количество объектов DataRowView, удовлетворяющих указанному критерию поиска. Между FindRows и Find имеются два существенных различия. Во-первых, FindRows может возвратить несколько объектов DataRowView. А во-вторых, FindRows возвращает массив объектов DataRowView, а метод Find возвращает целочисленный индекс.

Закрепим описания этих концепций на примере. можно создать самостоятельно, выполнив следующие несложные шаги:

1. Как обычно, вначале создайте Windows-приложение. Назовите его Exercise 8.8 и измените текст заголовка в главной форме приложения на “Exercise 8.8&#8243;.

2. Поместите на форму элемент DataGridView с именем dgView и четыре кнопки. Остановите для них следующие имена и надписи:

• btnLoad, Load Data {Загрузка данных)

• btnSort, Sort Data (Сортировка данных)

• btnFilter. Filter Data (Фшшграция данных}

• btnFindRows, Find Rows (Поиск строк}

Полученная форма должна выглядеть в окне конструирования так.

3. В этом примере элемент dgView будет привязан по данным к объекту DataView с именем CustomerView, сцепленным с объектом DataTable с именем CustomerTable. Объект CustomerView будет заполняться в обработчике события щелчка на кнопке Load Data. В обработчике события щелчка на btnLoad введите следующий код:
  
C#

private void btnSort Click(ob]ect sender, EventArgs e)

{

CustomersView.Sort = &#171;FirstName ASC&#187;;

}

VB.NET

Private Sub btnSort_Click(

ByVal sender As System.Object, ByVaj e As System.EventArgs)

Handles btnSort.Click CustomersView.Sort = &#171;FirstName ASC&#187;

End Sub

Скомпилируйте приложение и запустите его. Щелкните сначала на кнопке Load Data, а затем на кнопке Sort Data. После щелчка на Sort Data различные строки в элементе dgView будут отображаться в порядке их возрастания — как показано.
  
5. Теперь щелкните на кнопке Filter Data. Приложение попытается отфильтровать те строки, фамилия в которых заканчивается на “Of Jungle”. Как уже было показано, в RowFilcer нужно указать строку “LastName like 1 %0fJungle'&#187;. Это можно сделать с помощью следующего фрагмента кода:

> C#
> 
> private void btnFj. lter_Click (object sender, EventArgs e)
> 
> (
> 
> CustomersView.RowFilter = &#171;LastName like &#8216;%0fJunqle'&#187; ;
  
> c#
> 
> pr_vate voia ir. nl.oad Click (object sender, EventArgs e)
> 
> I
> 
> С istomersTable &#8212;
> 
> CreateDalaSet. DalaSet.Fillsr. Fii_Dat=set (datarile?a';.h} .Tab -e? { &#171;Castomers&#187;;; dgvie* . TataSource = Ci:stornr-:5Viev;;
> 
> }
> 
> VB.NET
> 
> Private Sab btnIcac_Clic<( RyVal sender As Systcrp.Object, By^al e As Syste-n.bventArgs) Handles btnload.Cl 1c< Custom^rsTable = CreateDataSpt.DataSetFiller.FiliDataset(dataFilePstn).Tables("Customers") CustomersVie1» = New DataVi ew (CusccrrersTabl^) dgVie1» .DjtaSource = Custorr.orsVicw Lnd Sub

Откомпилируйте и запустите приложение. После щелчка на кнопке Load Data приложение должно успешно загрузить данные из таблицы Customers и вывести их в элементе dgView.

4. Теперь попробуем отсортировать данные в приложении по столбцу F.. rstName в порядке возрастания. В обработчике события щелчка на кнопке btnSort введите следующий код:

> VB.NET
  
> Private Sub btnFilter\_Cli\_ck (
> 
> ByVal sender As System.Object, ByVal e As System.EventArgs) _
> 
> Handles btnFilter.Click
> 
> CustomersView.RowFilter &#8212; &#171;LastNarne like 1 %OfJungle’
> 
> End Sub

поскольку в джунглях живут только Тарзан и Джейн, приложение выведет только две строки, удоалетворяющие заданному фильтру строк.
  
6. И. наконец, приложение найдет строки с учетом ключа сортировки. Поскольку у нас ключом сортировки является столбец FirstName, попробуем найти имена клиентов, содержащие в этом столбце “Tarzan&#187;. Это можно сделать с помощью следующего фрагмента кода:

> C#
> 
> private void btnFindRows_Click(object sender, EventArgs e)
> 
> {
> 
> DataRowView [; drvs = CustomersView.FindRows(&#171;Tarzan&#187;); foreach (DataRowView drv in drvs)
> 
> [
> 
> MessageBox.Show(
> 
> drv.Row[&#171;FirstName&#187;] + &#187; &#187; + drv.Row[&#171;LastName”], &#171;Selected Item&#187;);
> 
> }
> 
> Private Sub btnFirdrtows C]ic<( ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnFinaRows.Clack Dim arvsO As DataRowView - CustomersView.FindRows("Tarzan") Dim drv As DataRowView For Each drv In drvs KessageBox.Shcw( _ drv.Row("FirstName") &#038; " " &#038; drv.Row("LastNarne") , "Selected Item") Next End Sub

Скомпилируйте и запустите приложение. Щелкните по тщ-.т.:*- &#8212;]

очереди на кнопках Load Data, Sort Data, Filter Data и Find Rows — и вы получите сообщение.

7. А теперь немого поразвлекаемся: запустите приложение еще раз, загрузите данные с помощью кнопки Load

Data, не сортируйте данные, по желанию отфильтруйте, Результат и попытайтесь выполнить метод FindRows для несорти- поиска потребителя рованных данных. Появится сообщение об исключении, с ь1менем Tarzan. В VB.NET будет получено аналогичное исключение.

Так что, как видите, для столбцов, для которых будет выполнен метод Find или FindRows, обязательно нужно указать порядок сортировки.

8. В качестве упражнения можно легко заменить метод FindRows на Find и получить аналогичные результаты. С помощью другого перегруженного варианта можно в порядке сортировки указать несколько столбцов и несколько критериев Find или FindRows.

И класс DataTable, и класс DataView позволяют также обновлять указанные в них данные аналогично такой же возможности в СУБД с помощью операторов DML INSERT, UPDATE и DELETE языка SQL. Эта возможность объектов DataView и DataSet будет подробно рассмотрена, где вы познакомитесь с обновлением данных и в подключенных, и в автономных ситуациях.