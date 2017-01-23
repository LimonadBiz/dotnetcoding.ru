---
title: Асинхронный запрос к большим наборам результатов
author: dotnetcoding
type: post
date: 2012-07-25T09:49:33+00:00
url: /coding/asinhronny-j-zapros-k-bol-shim-naboram-rezul-tatov.html
robotsmeta:
  - index,follow
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:1835:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">C<span style="color: #339900;">#</span>
    &nbsp;
    AsyncCallcack callback <span style="color: #000040;">-</span> <span style="color: #0000dd;">new</span> AsyrcCa<span style="color: #000040;">^</span>Iback<span style="color: #008000;">&#40;</span>DataReaaerlsReady<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span> TAsyncResult asyncresuj t <span style="color: #000080;">=</span>
    &nbsp;
    testCo<span style="color: #000040;">-</span>nmand.3eginbKccutcHeader <span style="color: #008000;">&#40;</span>callback, testConrr.<span style="color: #0000ff;">and</span><span style="color: #008000;">&#41;</span> <span style="color: #008080;">;</span>
    &nbsp;
    VB.<span style="color: #007788;">NET</span>
    &nbsp;
    Dim callback as AsyncCallbcck <span style="color: #000080;">=</span>
    &nbsp;
    nev<span style="color: #008080;">;</span> AsvncCaiiback<span style="color: #008000;">&#40;</span>DataReaaerlsReady<span style="color: #008000;">&#41;</span>
    &nbsp;
    Dim asyncresult as IAsyncResull <span style="color: #000080;">=</span>
    &nbsp;
    eestCcm<span style="color: #000040;">-</span>nand.<span style="color: #007788;">BeginExeci</span><span style="color: #000040;">-</span>teReader <span style="color: #008000;">&#40;</span>callbacx, testCommand<span style="color: #008000;">&#41;</span></pre></td></tr></table><p class="theCode" style="display:none;">C#
    
    AsyncCallcack callback - new AsyrcCa^Iback(DataReaaerlsReady); TAsyncResult asyncresuj t =
    
    testCo-nmand.3eginbKccutcHeader (callback, testConrr.and) ;
    
    VB.NET
    
    Dim callback as AsyncCallbcck =
    
    nev; AsvncCaiiback(DataReaaerlsReady)
    
    Dim asyncresult as IAsyncResull =
    
    eestCcm-nand.BeginExeci-teReader (callbacx, testCommand)</p></div>
    ";}
categories:
  - .NET Программирование

---
В предыдущих двух разделах было показано, как выбирать набор результатов с помощью компонента чтения данных. Упражнения работали очень хорошо, поскольку в наборе результатов было всего лишь три строки. А если бы это было 100 ООО строк?<!--more--> Работал бы предыдущий код? Конечно, работал бы. Единственная проблема в том, что минута-две уходили бы на вьшолнение команды выборки, а в это время вызывающий поток был бы блокирован. Если этот поток является потоком. используемым пользовательским интерфейсом (например, в однопотоковом приложении вроде примера), этот пользовательский интерфейс не смог бы даже выполнить свою перерисовку. Пользователь мог бы подумать, что приложение зависло и принудительно завершить выполнение приложения.

В .NET 1.1 эту проблему можно было разрешить, запустив еше один поток, создав в этом потоке отдельный компонент чтения данных и указав этому потоку уведомить главный поток о готовности к выборке данных. После этого для отображения данных следовало использовать метод Form. Invoke для переключения контекстов потока и связывания выбранных данных с пользовательским интерфейсом в контексте того потока, в котором создан пользовательский интерфейс.

Если вы не перечитали предыдущий абзац как минимум два раза, чтобы разобраться. что я только что сказал, то вы, наверно, крутой программист на .NET. Аесли вы хотя бы немного почесали голову — мужайтесь, ведь эго довольно сложный обходной путь для ситуации, которая может встречаться довольно часто. Поэтому в .NET 2.0 было введено асинхронное выполнение многих команд с помошью популярных методов Begin и типов данных TAsyncResult.

Теперь у нас есть запрос, который требует много времени на выполнение, и когда пользователь щелкнет па кнопке Populate Arraylist, нужно не блокировать пользовательский интерфейс, а выполнить метод BegmExecuteReader объекта SqlCommand, передав ему метод обратного вызова и объект команды- Метод обратного вызова — это метод, который вызывается после завершения выполнения команды. Таким образом мы сообшасм методу BegmExecuteReader: &#171;Начни выполнение метода, чтобы передать мне компонент чтения данных, а когда все будет готово, используй обратный вызов: и не забудь возвратить этот объект команды, чтобы я понял, о чем речь&#187;.

Посмотрим, как это выглядит в коде. Можно выполнить приведенные ниже четыре шага или загрузить код с web-сайта издательства под именем Exercise.
  
1. Начните с кода, написаппого для примера , и замените в нем вызов ExecuteReader на вызов BeginExecuteReader:

<pre lang="cpp">C#

AsyncCallcack callback - new AsyrcCa^Iback(DataReaaerlsReady); TAsyncResult asyncresuj t =

testCo-nmand.3eginbKccutcHeader (callback, testConrr.and) ;

VB.NET

Dim callback as AsyncCallbcck =

nev; AsvncCaiiback(DataReaaerlsReady)

Dim asyncresult as IAsyncResull =

eestCcm-nand.BeginExeci-teReader (callbacx, testCommand)
</pre>

Наибольшим преимуществом этого подхода является то, что поскольку вызов метода BegmExecuteReader не блокирует поток (т.е. вы не теряете контроль над потоком), во время выполнения запущенной команды можно продолжить обработку чею-то другого (например, перерисовывать пользовательский интерфейс).