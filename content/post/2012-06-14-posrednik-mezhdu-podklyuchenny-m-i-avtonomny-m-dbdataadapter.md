---
title: 'Посредник между подключенным и автономным: DbDataAdapter'
author: dotnetcoding
type: post
date: 2012-06-14T10:20:01+00:00
url: /coding/posrednik-mezhdu-podklyuchenny-m-i-avtonomny-m-dbdataadapter.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Класс DataAdapter — это посредник, или мостик, между подключенным и автономным мирами. <!--more-->Поскольку конкретная реализация адаптера данных зависит от соответствующего источника данных, конкретные адаптеры данных реализованы в составе поставщиков данных. Например, для Microsoft SQL Server нужен SqlDataAdapter, а для Oracle — OracleDataAdapter. Если нужен обобщенный доступ посредством ODBC или OleDb, то имеются специальнее адаптеры данных для обеспечения обобщенного доступа к данным в виде OdbcDaLaAdapter и OleDbDataAdapter.

Как и для всех других классов из подключенной части ADO.NET, общность всех этих различных классов обеспечивается общим базовым классом— классом DbDataAdapter- Этот принцип показан на рис. 2.7. Если у вас рябит в глазах от стрелок, попробуйте такой способ: закройте ладонью классы OracleCommand и OracIeDataAdapter, чтобы увидеть взаимосвязь между SgiCommand/Sql DataAdapter и DbCommand/DbDataAdapter. А теперь положите руку на классы SqlCommand и SqlDataAdapter. чтобы увидеть взаимосвязь между OracleCommdP.d/OracleDataAdapter и DbCommand/DbDataAdapter.

Классы SqiCornmand и OracleCommand, унаследованные от DbCommand. Для работы адаптеру данных нужны различные объекты DbCommand. Он может использовать до четырех DbCommand в свойствах TnsertCommand, &#8216;JpdateCommand, DeieteCommand и SelectCcmrnand для операторов INSERT. UPDATE. DELETE и SELECT. Эти четыре свойства типа DbCommand определены в классе DbDataAdapter — базовом для всех адаптеров данных.

Следуя традиции для всех подключенных объектов ADO.NET, конкретные адаптеры данных (SqlDataAdapter, OracIeDataAdapter и т.д.) также содержат четыре свойства с теми же именами — InsertCommand. UpdateComtr.and, DeleteCommand и SelectCommand — которые принимают объекты команд, зависящие от поставщика, такие как SqlCommand и OracleCommand.

&nbsp;

Важной частью любой архитектуры программирования является обработка ошибок. Для облегчения этой задачи в .NET имеется механизм обработки исключений (exception handling). ADO.NET, как и любая другая архитектура, содержит некоторое количество стандартных исключений для различных возможных ошибочных состояний. Рассмотрим различные доступные в ADO.NET исключения, которые могут вам пригодиться.