---
title: 'Заполнение DataSet: случай с более чем одной таблицей'
author: dotnetcoding
type: post
date: 2012-07-25T11:20:29+00:00
url: /coding/zapolnenie-dataset-sluchaj-s-bolee-chem-odnoj-tablitsej.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Как было сказано, объекты DataTable работают только для одной таблицы, но DataSet имеет возможность хранить не только несколько таблиц, но отношения между ними. Весь это механизм находится в тексте команды для соответствующего порожденного объекта DbCommand.<!--more--> Сейчас, чтобы заполнить DataSet не одной таблицей, а несколькими, можно просто взять код, заменить DataTable на DataSet и выполнить соответствующие изменения в CommandText. Понятно, что нельзя просто привязать DataSet непосредственно к элементу вроде DataGridview. поэтому изменится и логика отображения, но об этом чуть позже. Код для заполнения DataSet вместо DataTable приведен. Переменная userData теперь имеет тип DataSet.

**Программное заполнение DataSet** 

> на C#
> 
> private void butconFillData_Click(object sender, EventArgs e)
> 
> {
> 
> // He кодируйте жестко строки подключения // Выбирайте их из конфигурационного файла string comiectionStnng -’’Data Source=(local);Initial Catalog=Test;Integrated Security=SSPI;&#187;;
> 
> using (SqlConnection testConnection = new SqlConnection(connectionString))
> 
> {
> 
> SqlCommand testCommand = testConnection.CreateCommand(); testCommand.CommandText =• &#171;SELECT FirstName, LastName FROM userTable;&#187;
> 
> + &#187; SELECT PermissionType FROM PermissionsTable&#187;;
> 
> SqlDataAdapter dataAdapter = new SqlDataAdapter(testCommand); aataAdapter.Fill(userData);
> 
> ) // Метод testConnection.Dispose вызван автоматически

> Вообще-то это зависит от конкретного поставщика данных и исходного источника данных. Поэтому некоторые компоненты чтения данных не могут выбирать несколько наборов результатов за одно обращение к базе данных. Но в целях данного обсуждения мы предполагаем. что они чогуг выбирать несколько наборов результатов, как это делает SQL Server. Oracle или любая другая &#171;серьезная&#187; СУБД. 

.NET

> Private Sue buttonF-llData_Click (
> 
> ByVal sender As System.Object, ByVal e As System.EventArgs)
> 
> Handles buttonFillData.Click &#8216; He кодируйте жестко строки подключения 1 Выбирайте их из конфигурационного файла Dirn connectionString As String connectionString = _
> 
> &#171;Data source=(local) ,-Initial Catalog=Test;Integrated Serunty=SSPI;&#187; Using testConnection As SqlConnection = New SqlConnection(connectionString) Diir testCommand As SqlCommand =• testConnection .CreateCommand () testCommand.ConmandText = &#171;SELECT FirstName, LastName FROM userTable;&#187; £
> 
> ” SELECT PermisslonType FROM PermissionsTable”
> 
> Dim dataAdapter As New SqlDataAdapter(testCommand) dataAdapter.Fill(userData)
> 
> End Using &#8216; Метод testConnection.Dispose вызван автоматически End Sub

Листинги содержат код для поставщика данных Microsoft SQL Server. В них используется динамический SQL. но тот же результат можно получить и с помощью хранимой процедуры.

**Хранимая процедура для Microsoft SOL Server, возвращающая несколько результатов:**

> Create procedure GetMultipleResults As
> 
> Begin
> 
> SELECT FirstName, LastName FROM userTable;
> 
> SELECT PermissionType FROM PermissionsTable;

Как уже было сказано в связи с компонентами чтения данных, в Oracle этот же результат можно получить с помощью хранимой процедуры с несколькими REF CURSOR. Такой код приведен. Конечно, выборка одного результата с помощью хранимой процедуры Oracle требует возвращения лишь одного REF CURSOR.

**Пакет и хранимая процедура для Oracle, возвращающая несколько результатов**

> CREATE OR REPLACE PACKAGE USERPERMSPKG AS TYPE RESULTCURR IS REF CURSOR;
> 
> PROCEDURE GETUSERPERMS (USERCUR OUT RESULTCURR,
> 
> PERMSCUR OUT RESULTCURR) ;
> 
> END USERPERMSPKG;
> 
> CREATE OR REPLACE PACKAGE BODY USERPtRMSPKG AS
> 
> PROCEDURE GETUSERPERMS (USERCUR OUT RESULTCURR,
> 
> PERMSCUR OUT RESULTCURR)
> 
> IS
  
> LOCALUSERCUR RESULTCURR;
> 
> LOCALPERMSCUR RESULTCURR;
> 
> BEGIN
> 
> OPEN LOCALUSERCUR FOR
> 
> select firstname, lastname from uscrtable,-
> 
> OPEN LOCALPERMSCUR FOR
> 
> SELECT PERMISSIONTYPE FROM PERMISSIONSTABI,!’,; USERCUR := LOCALUSERCUR;
> 
> PERMSCUR := LOCALPERMSCUR;
> 
> END GETUSERPERMS;
> 
> END USERPERMSPKG;

Итак, просто заменив DataTable на DataSet и соответствующим образом изменив текст команды, можно вместо DataTable легко заполнить объект Databe i Однако в Oracle для этого нужно выполнить дополнительный шаг: указать дополни тельные параметры типа OracleType .Cursor в соответствующем SelectComrrana объекта OracleDataAdapter. Это нетрудно сделать с помощью такого кода:

C#

> dataAdapter.SelectComrnand.Parameters.Add(
> 
> new OracleParameter [&#171;USERCUR&#187;, OracleType.Cursor]1; dataAdapter.SelectComrnand.Parameters[0].Direction ~-ParameterDirection.Output; dataAdapter.SelectComrnand.Parameters.Add(
> 
> new OracleParameter[&#171;PERMSCUR&#187;, Oracle]ype.Cursor]); dataAdapter.SelectComrnand.Parameters[1].Direction -ParameterDirection.Output;

VB.NET

> dataAdapter.SelectComrnand.Parameters.Add( _
> 
> New OracleParameter(&#171;USERCUR”, OracleType.Cursor)) dataAdapter.SelectComrnand.Parameters(0).Direction = _
> 
> ParameterDirection.Output dataAdapter.SelectComrnand.Parameters.Add( _
> 
> New OracleParameter(&#171;PERMSCUR&#187;, OracleType.Cursor)) dataAdapter.SelectComrnand.Parameters(1).Direction &#8212; _
> 
> ParameterDirection.Output Но, оказывается, все еще интереснее!

Объект DataSet может содержать несколько объектов DataTable, заполненных из различных источников данных. Можно и не загружать все данные одно временно, но при автономной работе все-таки поддерживать отношения межд> различными DataTable. Но поскольку невозможно {или по крайней мере сложно) создать отношения DataRelation между двумя объектами DataTable из различ ных DataSet, видимо, нужен механизм для заполнения DataSet с помощью двух различных DbCommand за два обращения к различным базам данных.