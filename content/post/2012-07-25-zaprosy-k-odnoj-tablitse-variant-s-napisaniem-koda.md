---
title: 'Запросы к одной таблице: вариант с написанием кода'
author: dotnetcoding
type: post
date: 2012-07-25T11:15:38+00:00
url: /coding/zaprosy-k-odnoj-tablitse-variant-s-napisaniem-koda.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
мы напишем код самостоятельно. Вы убедитесь, что ручное написание кода дает больше возможностей управления запросами к базе данных и прияязкой по данным выбранного объекта DataTable к пользовательскому интерфейсу.<!--more--> Здесь и понадобится взаимодействие с объектом DataAdapter. Код для этого упражнения можно загрузить с web-санта издательства под именем Exercise 7.2. Но можно создать приложение, просто выполнив следующие шаги:

1. Начните с создания приложения на базе Windows-формы. Наловите его Exercise 7.2 и измените текст заголовка главной формы на Exercise 7.2.

2. На только что созданную главную форму добавьте элемент DataGridView и назовите его datagridView.

3. Теперь добавьте две кнопки: кнопку с именем buttonFillData и текстом Fill Data (Заполнение данными) и кнопку с именем buttonBind и текстом DataBind (Привязка по данным). После небольших изменений размера и положения управляющих элементов форма должна выглядеть так, как показано
  
4. Перейдем к коду для этой формы. Щелкните на форме правой кнопкой и выберите пункт View Code (Просмотр кода). Вы увидите частичную реализацию класса для Forml. cs (или . vb). Добавьте сюда операторы using или import
  
для пространств имен System. Data и System. Data. SqlClient. Кроме того, добавьте в класс userTable приватную переменную userTable типа DataTable и внесите в конструктор код ее создания:

C#

partial class Forml : Form {

private DataTable userTable; public Forml()

{

ImtializeComponent (); userTable &#8212; new DataTable () ;

}

VB.NET

Public Class Forml

private userData As New DataTable

End Class

5. Теперь возвратитесь к конструктору формы и дважды щелкните на кнопке Fitt Data (buttonFillData), чтобы создать обработчик события щелчка на этой кнопке. В этом обработчике напишите код заполнения объекта DataTable. Этот код приведен в листингах 7.1 и 7.2.

 **Программное заполнение экземпляра userTable** 
  
на

> C# privace voia buttonFillData_Click(object sender, EventArgs e)
> 
> {
> 
> // He колируйте жестко строки подключения // Выбирайте их из конфигурационного файла string connectionString —
> 
> &#171;Data Source=(local);Imtial Catalog=Test;Integrated Security=SSPI;&#187;;
> 
> using (SqlConnection testConnection = new SqlConnection(connectionString))
> 
> {
> 
> SqlCommand testComrcand &#8212; testConnection.CreateCommand0; testCommand.CommandText = &#171;SELECT FirstName, LastName FROM userTable&#187;; SqlDataAdapter dataAdapter &#8212; new SqlDataAdapter(testCcmmand); dataAdapter.Fill(userTable);
> 
> } // Метод testConnection.Dispose вызван автоматически 

> на Visual Basic .NET
  
> Drivate Sub buttonFillData\_Click( \_
> 
> ByVal sender As System.Object, ByVal g As System.EventArgs) _
> 
> Handles buttonFillData.Click ’ He кодируйте жестко строки подключения ’ Выбирайте их из конфигурационного файла Dim connectionString As String connectionString = _
> 
> &#171;Data Source-(local);Initial Catalog-Iest;Integrated Secunty-SSPI;&#187;
> 
> Using testConnection As SqlConnection &#8212; tCew SqlConnection(connectionString) Dim testCommand As SqlCommand = tesLConnectjon.CreateComrnand () testCommand.Commandlext = &#187;SELECT FirstName, LastName FROM UserTable”
> 
> Dim dataAdapter As New sqlDataAdapter(testCommand) dataAaaptet.Fi11(userData)
> 
> End Using &#8216; Метод testConnection.Dispose вызван автоматически End Sab 

6. He выхода из конструктора формы, дважды щелкнете на кнопке DataBind {but-tonBind), чтобы создать обработчик события щелчка на этой кнопке. В этом обработчике напишите код привязки по данным элемента DataGridView к объекту userTable:

> C#
> 
> Drivate void buttonBind_Click (object sender, EventArgs e) datagridView.DataSource &#8212; userTable;
  
> VB.NET
> 
> Private Sub buttonBind_Click (
> 
> 3yVal sender As System.Object, ByVal e As System.EventArgs)
> 
> Handles buttonBind.Click datagridView.DataSoarce = userData End Sub

7. Скомпилируйте и запустите приложение.

8. В качестве упражнения замените userTable типа DataTable на DataSet и выполните соответствующие изменения в коде DataBind. Вы увидите, что DataAdapter может заполнять как DataTable. так и DataSet.