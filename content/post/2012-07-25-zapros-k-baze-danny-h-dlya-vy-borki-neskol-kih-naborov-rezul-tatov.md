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
