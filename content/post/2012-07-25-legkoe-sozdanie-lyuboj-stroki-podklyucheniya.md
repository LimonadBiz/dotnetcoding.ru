---
title:
  - Легкое создание любой строки подключения
author: dotnetcoding
type: post
date: 2012-07-24T20:57:14+00:00
url: /coding/legkoe-sozdanie-lyuboj-stroki-podklyucheniya.html
description:
  - Классы генераторов строк подключения для конкретных поставщиков данных позволяют легко создавать строки подключения для соответствующих СУБД
robotsmeta:
  - index,follow
wp-syntax-cache-content:
  - |
    a:2:{i:1;s:1987:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;"><span style="color: #008000;">&#91;</span>oledb
    &nbsp;
    <span style="color: #008080;">;</span> Everything after <span style="color: #0000dd;">this</span> line is an OLE ЭВ jnitstr<span style="color: #000040;">-</span>ng <span style="color: #008080;">;</span> Все после этой строки <span style="color: #000040;">-</span> строка инициализации OLE DB ProvLder<span style="color: #000080;">=</span>Kacrosoft.<span style="color: #007788;">Jet</span>.<span style="color: #007788;">OLEDB</span>.4.0<span style="color: #008080;">;</span>Password<span style="color: #000040;">-</span><span style="color: #FF0000;">&quot;&quot;</span><span style="color: #008080;">;</span>
    &nbsp;
    Data source<span style="color: #000040;">-</span>C<span style="color: #008080;">:</span>ApreosMyd£<span style="color: #000080;">&gt;</span>.<span style="color: #007788;">mdb</span><span style="color: #008080;">;</span>Persibt Security Info<span style="color: #000080;">=</span><span style="color: #008080;">?</span>rue
    Вот и все. Теперь можно скопировать строку подключения, вставить ее в код и выполнить подключение к базе данных Microsoft Access<span style="color: #008080;">:</span></pre></td></tr></table><p class="theCode" style="display:none;">[oledb
    
    ; Everything after this line is an OLE ЭВ jnitstr-ng ; Все после этой строки - строка инициализации OLE DB ProvLder=Kacrosoft.Jet.OLEDB.4.0;Password-&quot;&quot;;
    
    Data source-C:ApreosMyd£&gt;.mdb;Persibt Security Info=?rue
    Вот и все. Теперь можно скопировать строку подключения, вставить ее в код и выполнить подключение к базе данных Microsoft Access:</p></div>
    ";i:2;s:1081:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">OleDbConnection testConnection <span style="color: #000080;">=</span> <span style="color: #FF0000;">'lew OieDcConnf’ction (&quot;Provider^Microsoft.Jet.GLEDB.4.0;&quot; +
    &nbsp;
    Data Source=C:<span style="color: #000099; font-weight: bold;">\</span>Apress<span style="color: #000099; font-weight: bold;">\</span>myab.mdb;Persist Security Info=Fdlse&quot;); VB.NET
    &nbsp;
    Tim testConnec-ion As New OleDbConnectior (
    &nbsp;
    Provider=Microsoft. Jet. OLEDB. 4 .0;
    &nbsp;
    Data Sojrce=C:Apressmydb.mdb;i?ersist Security Info=False&quot;)</span></pre></td></tr></table><p class="theCode" style="display:none;">OleDbConnection testConnection = 'lew OieDcConnf’ction (&quot;Provider^Microsoft.Jet.GLEDB.4.0;&quot; +
    
    Data Source=C:\Apress\myab.mdb;Persist Security Info=Fdlse&quot;); VB.NET
    
    Tim testConnec-ion As New OleDbConnectior (
    
    Provider=Microsoft. Jet. OLEDB. 4 .0;
    
    Data Sojrce=C:Apressmydb.mdb;i?ersist Security Info=False&quot;)</p></div>
    ";}
categories:
  - .NET Программирование

---
