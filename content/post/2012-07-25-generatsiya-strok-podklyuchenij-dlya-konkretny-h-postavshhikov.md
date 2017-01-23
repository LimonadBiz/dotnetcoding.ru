---
title:
  - 'SQLConnectionStringBuilder - Генерация строк подключений для конкретных поставщиков'
author: dotnetcoding
type: post
date: 2012-07-24T20:51:42+00:00
url: /coding/generatsiya-strok-podklyuchenij-dlya-konkretny-h-postavshhikov.html
keywords:
  - SQLConnectionStringBuilder
description:
  - 'В строках подключения может быть указано множество различных параметров. Для успешного установления подключения к базе данных каждый из этих параметров нужно правильно назвать и указать для него верное значение. '
robotsmeta:
  - index,follow
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:6236:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;"><span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Main<span style="color: #008000;">&#40;</span>string<span style="color: #008000;">&#41;</span><span style="color: #008000;">&#93;</span> args<span style="color: #008000;">&#41;</span>
    &nbsp;
    SqlConnectionStrmgBuilder ccr.<span style="color: #007788;">nstrBuilder</span> <span style="color: #000040;">-</span><span style="color: #0000dd;">new</span> SqlConncctionS LringBuilder<span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span> connstrBuiider.<span style="color: #007788;">DatdSourcc</span> <span style="color: #000080;">=</span> <span style="color: #FF0000;">&quot;(local)&quot;</span><span style="color: #008080;">;</span> connstrRuildpr. <span style="color: #007788;">Inn</span> rialCatdlog <span style="color: #000080;">=</span> <span style="color: #FF0000;">&quot;'Test&quot;</span><span style="color: #008080;">;</span> connstrBuilder.<span style="color: #007788;">InleqratedSecurity</span> <span style="color: #000040;">-</span> <span style="color: #0000ff;">true</span><span style="color: #008080;">;</span>
    &nbsp;
    <span style="color: #0000ff;">using</span> <span style="color: #008000;">&#40;</span>SqlCornection tesIConnectior <span style="color: #000080;">=</span>
    &nbsp;
    <span style="color: #0000dd;">new</span> SqI Connection<span style="color: #008000;">&#40;</span>corns trBuildcr.<span style="color: #007788;">ToString</span> <span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span>
    &nbsp;
    <span style="color: #0000ff;">try</span>
    &nbsp;
    LestConr.<span style="color: #007788;">cctior</span>, .<span style="color: #007788;">Open</span> <span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span> <span style="color: #008080;">;</span>
    &nbsp;
    <span style="color: #0000ff;">if</span> <span style="color: #008000;">&#40;</span>testConnection.<span style="color: #007788;">State</span> <span style="color: #000080;">==</span> ConnectienState.<span style="color: #007788;">Open</span><span style="color: #008000;">&#41;</span>
    &nbsp;
    <span style="color: #008000;">&#123;</span>
    &nbsp;
    Console.<span style="color: #007788;">WriteLine</span><span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;Connection successfully opened&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
    <span style="color: #666666;">// Подключение успешно открыто</span>
    &nbsp;
    Console.<span style="color: #007788;">WriteLinef</span><span style="color: #FF0000;">&quot;Connects on string used: &quot;</span> <span style="color: #000040;">+</span>
    &nbsp;
    <span style="color: #666666;">// Использована строка подключения testConnection.Connectlon.String) ;</span>
    <span style="color: #0000ff;">catch</span> <span style="color: #008000;">&#40;</span>Exception<span style="color: #008000;">&#41;</span>
    &nbsp;
    <span style="color: #008000;">&#123;</span>
    &nbsp;
    <span style="color: #0000ff;">if</span> <span style="color: #008000;">&#40;</span>tcstConnect_on.<span style="color: #007788;">Stace</span> <span style="color: #000040;">!</span><span style="color: #000080;">=</span> Conneo<span style="color: #000040;">-</span>ionState.<span style="color: #007788;">Open</span><span style="color: #008000;">&#41;</span>
    &nbsp;
    <span style="color: #008000;">&#123;</span>
    &nbsp;
    ConsoJс.<span style="color: #007788;">WriteLine</span><span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;Connection successfully failed&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
    <span style="color: #666666;">// Невозможно открыть подключение</span>
    &nbsp;
    Console.<span style="color: #007788;">vJriteLine</span><span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;Cornection scring ased: &quot;</span>
    &nbsp;
    <span style="color: #666666;">// Использована строка подключения + testConnectior.ConnoctionString);</span>
    <span style="color: #666666;">//Автоматический вызов освобождения подключения гарантирует его закрытие Console.WriteLine(&quot;Press ary key to continue...&quot;);</span>
    &nbsp;
    <span style="color: #666666;">// Для продолжения нажмите л&amp;бую клавишу Console.Reaai);</span></pre></td></tr></table><p class="theCode" style="display:none;">static void Main(string)] args)
    
    SqlConnectionStrmgBuilder ccr.nstrBuilder -new SqlConncctionS LringBuilder(); connstrBuiider.DatdSourcc = &quot;(local)&quot;; connstrRuildpr. Inn rialCatdlog = &quot;'Test&quot;; connstrBuilder.InleqratedSecurity - true;
    
    using (SqlCornection tesIConnectior =
    
    new SqI Connection(corns trBuildcr.ToString ()))
    
    try
    
    LestConr.cctior, .Open () ;
    
    if (testConnection.State == ConnectienState.Open)
    
    {
    
    Console.WriteLine(&quot;Connection successfully opened&quot;);
    
    // Подключение успешно открыто
    
    Console.WriteLinef&quot;Connects on string used: &quot; +
    
    // Использована строка подключения testConnection.Connectlon.String) ;
    catch (Exception)
    
    {
    
    if (tcstConnect_on.Stace != Conneo-ionState.Open)
    
    {
    
    ConsoJс.WriteLine(&quot;Connection successfully failed&quot;);
    
    // Невозможно открыть подключение
    
    Console.vJriteLine(&quot;Cornection scring ased: &quot;
    
    // Использована строка подключения + testConnectior.ConnoctionString);
    //Автоматический вызов освобождения подключения гарантирует его закрытие Console.WriteLine(&quot;Press ary key to continue...&quot;);
    
    // Для продолжения нажмите л&amp;бую клавишу Console.Reaai);</p></div>
    ";}
categories:
  - .NET Программирование
tags:
  - SQLConnectionStringBuilder

---
