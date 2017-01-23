---
title: Создание объектов подключения в ADO.NET
author: dotnetcoding
type: post
date: 2012-07-20T08:52:44+00:00
url: /coding/sozdanie-ob-ektov-podklyucheniya-v-ado-net.html
robotsmeta:
  - index,follow
wp-syntax-cache-content:
  - |
    a:5:{i:1;s:542:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">SqlConrertion LestConnection <span style="color: #000080;">=</span> <span style="color: #0000dd;">new</span> SqlCcnnscr.<span style="color: #007788;">ion</span> <span style="color: #008000;">&#123;</span><span style="color: #008000;">&#41;</span> <span style="color: #008080;">;</span></pre></td></tr></table><p class="theCode" style="display:none;">SqlConrertion LestConnection = new SqlCcnnscr.ion {) ;</p></div>
    ";i:2;s:320:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">Dim testConr.<span style="color: #007788;">ection</span> As New SqiConnection</pre></td></tr></table><p class="theCode" style="display:none;">Dim testConr.ection As New SqiConnection</p></div>
    ";i:3;s:1033:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">SqlConnection testConnection <span style="color: #000080;">=</span> <span style="color: #0000dd;">new</span> Sql cornecUcn <span style="color: #0000dd;">0</span> <span style="color: #008080;">;</span>
    &nbsp;
    strino testConnectionStnnq <span style="color: #000040;">-</span>
    &nbsp;
    <span style="color: #FF0000;">&quot;Data Source=(local);Initial Catalog-iest;Irtegratea Secunty-SSPl&quot;</span><span style="color: #008080;">;</span>
    &nbsp;
    testConnection.<span style="color: #007788;">ConnectionString</span> <span style="color: #000080;">=</span> testConnectionString<span style="color: #008080;">;</span></pre></td></tr></table><p class="theCode" style="display:none;">SqlConnection testConnection = new Sql cornecUcn 0 ;
    
    strino testConnectionStnnq -
    
    &quot;Data Source=(local);Initial Catalog-iest;Irtegratea Secunty-SSPl&quot;;
    
    testConnection.ConnectionString = testConnectionString;</p></div>
    ";i:4;s:1020:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">Dim testConnection As New SqlConnection
    &nbsp;
    Dim testConnectionStrmg As String <span style="color: #000080;">=</span> <span style="color: #FF0000;">&quot;Data Source-(local) ;	&amp;
    &nbsp;
    &quot;</span>Initial Cataiog<span style="color: #000040;">-</span>Iesc<span style="color: #008080;">;</span>Integrated S<span style="color: #000080;">&lt;</span><span style="color: #008080;">?</span>c<span style="color: #000040;">-</span>jrity<span style="color: #000080;">=</span>SSPI<span style="color: #FF0000;">&quot;
    &nbsp;
    testConnection.ConnectionString = testConnectionString</span></pre></td></tr></table><p class="theCode" style="display:none;">Dim testConnection As New SqlConnection
    
    Dim testConnectionStrmg As String = &quot;Data Source-(local) ;	&amp;
    
    &quot;Initial Cataiog-Iesc;Integrated S&lt;?c-jrity=SSPI&quot;
    
    testConnection.ConnectionString = testConnectionString</p></div>
    ";i:5;s:1092:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">SqlConnection teatConnection<span style="color: #000080;">=</span> <span style="color: #0000dd;">new</span> SqlConnection <span style="color: #008000;">&#40;</span>
    &nbsp;
    <span style="color: #FF0000;">&quot;Data Source=(local);Initial Cataloguest;Integratea Seourity-SSPI&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
    VB.<span style="color: #007788;">NET</span>
    &nbsp;
    Dim testConnection As New SqlConnection<span style="color: #008000;">&#40;</span>
    &nbsp;
    <span style="color: #FF0000;">&quot;Datd Sourcs=(local);Initial Catalog-I'est; Integrated Secunty-SSPI'')</span></pre></td></tr></table><p class="theCode" style="display:none;">SqlConnection teatConnection= new SqlConnection (
    
    &quot;Data Source=(local);Initial Cataloguest;Integratea Seourity-SSPI&quot;);
    
    VB.NET
    
    Dim testConnection As New SqlConnection(
    
    &quot;Datd Sourcs=(local);Initial Catalog-I'est; Integrated Secunty-SSPI'')</p></div>
    ";}
categories:
  - .NET Программирование

---
ADO.NET оформляет функции установления подключений к конкретной базе данных в виде типичного класса подключения. Давайте создадим экземпляр класса — т.е. объект — подключения. Пример для класса SqLConnection но базовые концепции в других классах подключения для различных поставщиков такие же. Различные объекты подключения можно создавать, создавая новые экземпляры соответствующих классов подключения.<!--more--> Вот как это делается:


  
C#

<pre lang="cpp">SqlConrertion LestConnection = new SqlCcnnscr.ion {) ;</pre>

VB.NET

<pre lang="cpp">Dim testConr.ection As New SqiConnection</pre>

Все очень просто: но, как вы, видимо, догадались, это еще не все, т.к. мы не указали объекту подключения, к какой базе данных нужно подключиться, какие права доступа использовать и т.д. Эти параметры можно задать с помощью свойства ConnectionString объекта SqLConnection:

C#

<pre lang="cpp">SqlConnection testConnection = new Sql cornecUcn 0 ;

strino testConnectionStnnq -

"Data Source=(local);Initial Catalog-iest;Irtegratea Secunty-SSPl";

testConnection.ConnectionString = testConnectionString;
</pre>

VB.NET

<pre lang="cpp">Dim testConnection As New SqlConnection

Dim testConnectionStrmg As String = "Data Source-(local) ;	&#038;

"Initial Cataiog-Iesc;Integrated S<?c-jrity=SSPI"

testConnection.ConnectionString = testConnectionString
</pre>


<p>
  Этот код подютавливает объект подключения к открытию подключения к SQL Server на локальной машине с помощью Windows-аутентификации и к подключению к базе данных с именем Test. Но вместо него можно воспользоваться одним из конструкторов класса SqlConnecti on и получить уже готовый объект
</p>


<p>
  <strong>SqlConnection:</strong>
</p>


<p>
  C#
</p>


<pre lang="cpp">
SqlConnection teatConnection= new SqlConnection (

"Data Source=(local);Initial Cataloguest;Integratea Seourity-SSPI");

VB.NET

Dim testConnection As New SqlConnection(

"Datd Sourcs=(local);Initial Catalog-I'est; Integrated Secunty-SSPI'')</pre>


<p>
  Итак можно будет подключить готовый объект SqiConnection с помощью лишь одной строки кода. А теперь, имея подготовленный таким образом объект подключения, для открытия подключения к указанной базе данных нужно лишь вызвать метод Open.
</p>