---
title: Выборка скалярного значения
author: dotnetcoding
type: post
date: 2012-07-25T09:42:45+00:00
url: /coding/vy-borka-skalyarnogo-znacheniya.html
robotsmeta:
  - index,follow
wp-syntax-cache-content:
  - |
    a:2:{i:1;s:482:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">SqlCommand testCommand <span style="color: #000080;">=</span> <span style="color: #0000dd;">new</span> SqlCommand <span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span></pre></td></tr></table><p class="theCode" style="display:none;">SqlCommand testCommand = new SqlCommand ();</p></div>
    ";i:2;s:357:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">Dim testCommand As New SqlConmand <span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span></pre></td></tr></table><p class="theCode" style="display:none;">Dim testCommand As New SqlConmand ()</p></div>
    ";}
categories:
  - .NET Программирование

---
Для выполнения запроса к базе данных нужен объект команды. Обсуждение в данной главе в основном касается Microsoft SQL Server, но описываемые концепции применимы к любым распространенным в ADO.NET поставщикам данных. <!--more-->Обобщенный объект команды в ADO-NET представлен классом DbCommand, а объекты команд, специфичные для Microsoft SQL Server, собраны в классе System. Data. SqlClient. SqlCommand. наследуемом от DbCommand. Приведено визуальное представление структуры наследования между SqlCommand, DbCommand и другими подобными классами.

Создать объект команды просто: нужно создать экземпляр класса, воспользовавшись одиим из четырех поддерживаемых перегруженных вариантов конструктора. В простейшей форме этот код может выглядеть так:

C#

<pre lang="cpp">SqlCommand testCommand = new SqlCommand ();
</pre>

VB.NET

<pre lang="cpp">Dim testCommand As New SqlConmand ()
</pre>

Этот код можно скомпилировать, но он не выполняет никаких действий. Теперь остановимся на минуту и обдумаем минимальные требования для успешного выполнения любой команды:

• Она должна выполниться по отношению к базе данных — но мы не указали, какое подключение должна использовать команда для своего выполнения.

• Необходимо указать действие, выполняемое командой — но мы (пока) не указали текст команды.

Так что, по крайней мере, нужно указать подключение, которое должен использовать объект команды, и действие, которое он должен выполнить. Начнем с первой части необходимой информации — базы данных, по отношению к которой должна быть выполнена команда.