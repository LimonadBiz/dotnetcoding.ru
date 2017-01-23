---
title: Запрос к базе данных для выборки нескольких наборов результатов
author: dotnetcoding
type: post
date: 2012-07-25T09:54:52+00:00
url: /coding/zapros-k-baze-danny-h-dlya-vy-borki-neskol-kih-naborov-rezul-tatov.html
robotsmeta:
  - index,follow
wp-syntax-cache-content:
  - |
    a:2:{i:1;s:1438:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">C<span style="color: #339900;">#</span>
    &nbsp;
    Sq_Command cmd <span style="color: #000080;">=</span>
    &nbsp;
    <span style="color: #0000dd;">new</span> SqlConnnana<span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;SELECT * FROM USERBASICINFORMATION&quot;</span> <span style="color: #000040;">+</span>	<span style="color: #000040;">+</span>
    &nbsp;
    <span style="color: #FF0000;">&quot;2EL5CT * FROM PKRM1 S3.1'OtCS TABLE&quot;</span> , conn<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
    VB.<span style="color: #007788;">NET</span>
    &nbsp;
    Dim cmd as sqlCo<span style="color: #000040;">-</span>mrand <span style="color: #000080;">=</span> _
    &nbsp;
    New SqJ Comma<span style="color: #FF0000;">'id(&quot;SELECT * FROM USERBASICINFORKATTON&quot; S	&amp; _
    &nbsp;
    &quot;SELECT '</span> FROM PERMI3SI0K3TABLE<span style="color: #FF0000;">&quot;, conn)</span></pre></td></tr></table><p class="theCode" style="display:none;">C#
    
    Sq_Command cmd =
    
    new SqlConnnana(&quot;SELECT * FROM USERBASICINFORMATION&quot; +	+
    
    &quot;2EL5CT * FROM PKRM1 S3.1'OtCS TABLE&quot; , conn);
    
    VB.NET
    
    Dim cmd as sqlCo-mrand = _
    
    New SqJ Comma'id(&quot;SELECT * FROM USERBASICINFORKATTON&quot; S	&amp; _
    
    &quot;SELECT ' FROM PERMI3SI0K3TABLE&quot;, conn)</p></div>
    ";i:2;s:2587:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">CREATE OR REPLACE PACKAGE CserPermsP<span style="color: #000080;">&lt;</span>g AS L’YPI<span style="color: #000040;">-</span>’ HesultCu<span style="color: #000040;">-</span>r <span style="color: #000040;">-</span>S R<span style="color: #008080;">?</span>.<span style="color: #007788;">F</span> CURSOR<span style="color: #008080;">;</span>
    &nbsp;
    PROCEDURE GetJserPerns <span style="color: #008000;">&#40;</span>UserCur CUT ResultCurr,
    &nbsp;
    PerrrsCur OUT ResultCurr<span style="color: #008000;">&#41;</span> <span style="color: #008080;">?</span>
    &nbsp;
    END UserPerrrbPkq<span style="color: #008080;">;</span>
    &nbsp;
    CREATE OR REPLACE PACXAGi BODY UsorPcrmsPxg AS PROCEDURE Get<span style="color: #FF0000;">'JserPerns (UsorC'</span>ir CUT ResultCurr,
    &nbsp;
    PerrrsCur OCT ResultCurr<span style="color: #008000;">&#41;</span>
    &nbsp;
    IS
    &nbsp;
    I,oca <span style="color: #0000dd;">1</span> UserCur Rasa <span style="color: #0000dd;">1</span> rCurr<span style="color: #008080;">;</span>
    &nbsp;
    LocalPermsCur ResultCurr<span style="color: #008080;">;</span>
    BEGIN
    &nbsp;
    OPEN LocalUserCur FOR
    &nbsp;
    SELKCT <span style="color: #000040;">*</span> FROM USERBASIС INFORMATION<span style="color: #008080;">;</span>
    &nbsp;
    OPEN LocalPermsCur FOR
    &nbsp;
    SELECT <span style="color: #000040;">*</span> FROM PERMISSIONSTABLE<span style="color: #008080;">;</span>
    &nbsp;
    UserCur <span style="color: #008080;">:</span><span style="color: #000080;">=</span> LocalUserCur<span style="color: #008080;">;</span>
    &nbsp;
    PermsCur <span style="color: #008080;">:</span><span style="color: #000080;">=</span> LocalPermsCur<span style="color: #008080;">;</span>
    &nbsp;
    END GetUserPerms<span style="color: #008080;">;</span>
    &nbsp;
    END UserPermsPkg<span style="color: #008080;">;</span></pre></td></tr></table><p class="theCode" style="display:none;">CREATE OR REPLACE PACKAGE CserPermsP&lt;g AS L’YPI-’ HesultCu-r -S R?.F CURSOR;
    
    PROCEDURE GetJserPerns (UserCur CUT ResultCurr,
    
    PerrrsCur OUT ResultCurr) ?
    
    END UserPerrrbPkq;
    
    CREATE OR REPLACE PACXAGi BODY UsorPcrmsPxg AS PROCEDURE Get'JserPerns (UsorC'ir CUT ResultCurr,
    
    PerrrsCur OCT ResultCurr)
    
    IS
    
    I,oca 1 UserCur Rasa 1 rCurr;
    
    LocalPermsCur ResultCurr;
    BEGIN
    
    OPEN LocalUserCur FOR
    
    SELKCT * FROM USERBASIС INFORMATION;
    
    OPEN LocalPermsCur FOR
    
    SELECT * FROM PERMISSIONSTABLE;
    
    UserCur := LocalUserCur;
    
    PermsCur := LocalPermsCur;
    
    END GetUserPerms;
    
    END UserPermsPkg;</p></div>
    ";}
categories:
  - .NET Программирование

---
В последнем рассмотренном примере одним из способов выполнения запроса к независимым наборам результатов было два обращения к серверу и выполнение двух отдельных команд работы с базой данных Этот способ вполне работоспособен, однако представьте себе такую ситуацию&#8230;<!--more-->

Лет 5-10 назад, когда большинство из нас работало по телефонному модему, пользователю, находящемуся в США, нужно было примерно полсскунды на пингование сервера в Токио. Но загрузка полумегабайтного файла требовала от того же пользователя примерно полчаса работы с таким подключением. Сейчас у нас может быть оптоволоконный кабель, протянутый до самого компьютера, но при пинговании того же сервера в Токио требуется все так же полсекунды, хотя загрузка полумегабайтного файла занимает уже лишь несколько секуид. На время написания этой книги ученые не изобрели легкого способа превышения скорости света, так что можно смсло предположить, что время пингования вряд ли существенно сократится в ближайшем будущем, хотя скорости загрузки будут продолжать расти.
  
Если применить все сказанное в предыдущем абзаце к ADO.NET, то несколько обращений к базе данных для выборки какого-то количества данных гораздо более ресурсоемко, чем одно обращение к базе для выборки того же количества данных. Именно поэтому лучше беседовать с базой данных длинными монологами, а не прерывающимся диалогом.

> Совет. Во всех случаях автономных вычислений старайтесь общаться монологами, а не диалогом. 

Итак, нам нужен легкий способ выборки нескольких наборов данных за одно обращение к базе. Для этого рассмотрим упражнение, в котором будут выполняться запросы к двум таблицам — Use г Basic in formation и PermissionsTable — из локальной базы данных Test. Код этого упражнения можно загрузить с web-сайта издательства под именем Exercise 5.5 или создать самостоятельно, выполнив сле-дующие шаги:
  
1. Начните с кода из примера 5.2 (в этом примере демонстрировалась работа компонента чтения данных с одним набором результатов), и измените текст команды из SqlCom.vancl па следующий:

<pre lang="cpp">C#

Sq_Command cmd =

new SqlConnnana("SELECT * FROM USERBASICINFORMATION" +	+

"2EL5CT * FROM PKRM1 S3.1'OtCS TABLE" , conn);

VB.NET

Dim cmd as sqlCo-mrand = _

New SqJ Comma'id("SELECT * FROM USERBASICINFORKATTON" S	&#038; _

"SELECT ' FROM PERMI3SI0K3TABLE", conn)
</pre>

Как в иди re. вое изменение свелось к конкатенации двух командных строк с символом &#187; между ними. Такой текст в Microsoft SQL Server обычно называется пакегимои командой SQL (batched SQL command). В Oracle пакетные запросы пока поддерживаются, но в будущем эта поддержка прекратится. Если в Oracle нужно возвратить несколько наборов данных, ггридется создать хранимую процедуру, которая в качестве множественного результата возвращает REF CCRSCR:

<pre lang="cpp">CREATE OR REPLACE PACKAGE CserPermsP&lt;g AS L’YPI-’ HesultCu-r -S R?.F CURSOR;

PROCEDURE GetJserPerns (UserCur CUT ResultCurr,

PerrrsCur OUT ResultCurr) ?

END UserPerrrbPkq;

CREATE OR REPLACE PACXAGi BODY UsorPcrmsPxg AS PROCEDURE Get'JserPerns (UsorC'ir CUT ResultCurr,

PerrrsCur OCT ResultCurr)

IS

I,oca 1 UserCur Rasa 1 rCurr;

LocalPermsCur ResultCurr;
BEGIN

OPEN LocalUserCur FOR

SELKCT * FROM USERBASIС INFORMATION;

OPEN LocalPermsCur FOR

SELECT * FROM PERMISSIONSTABLE;

UserCur := LocalUserCur;

PermsCur := LocalPermsCur;

END GetUserPerms;

END UserPermsPkg;

</pre>

При наличии такой хранимой процедуры можно воспользоваться объектом OracleDataReader и работать с несколькими наборами результатов с помощью одного OracleDataReader, просматривая все результаты методом NextResult.

2. Следующее изменение — чтение из SqlDataReader нескольких наборов результатов. В объекте SqlDataReader имеется метод NextResul t, который позволяет перейти к следующему набору результатов. Если это был последний набор результатов, метод возвращает false.
  
Итак, не выполняя несколько компонентов чтения данных, мы смогли выбрать несколько наборов результатов в одном компоненте чтения данных. Это особенно удобно при работе с автономными данными наподобие DataSet, в котором больше одного объекта DataTable. 

Одной интересной особенностью всех приведенных до сих пор примеров является то, что единственными типами выбираемых данных являлись типы, родные для конкретной СУБД. Они также называются встроенными скалярными типами. Мы уже рассмотрели запрос строки, набора результатов и нескольких наборов результатов — и во всех этих случавх выбираемые данные имели лишь встроенные скалярные тэтты-

Однако при объектно-ориентированной разработке (Object-Oriented Development — OOD) большинство бизнес-объектов представляются с помощью представления отображения объектов. Это иерархическое отображение обьектов обычно требует трансляции в обычную реляционную структуру в базе данных и назад; этот процесс обычно называется O/R-отображением (Object-Relational Mapping— объектно-реляционное отображение). СУБД работают с реляционными структурами, а в приложениях работа в основном ведется с объектными представлениями данных.

Итак, налицо противоречие.