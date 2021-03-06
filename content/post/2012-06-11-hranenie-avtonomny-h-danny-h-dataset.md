---
title: 'Хранение автономных данных: DataSet'
author: dotnetcoding
type: post
date: 2012-06-11T09:47:48+00:00
url: /coding/hranenie-avtonomny-h-danny-h-dataset.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Как было сказано, ADO.NET можно разбить на две большие части: подключенную и автономную.<!--more--> Класс подключения, класс команды, класс транзакции и класс параметра, а также некоторые другие, формирующие поставщик данных — это классы, которые требуют для своей работы подключения к источнику данных.

Команды подразделяются на три основные категории: язык определения данных (Data Definition Language — DDL), используемый для определения структуры базы данных; язык манипуляции данными (Data Manipulation Language — DML), используемый для выполнения запросов вроде UPDATE, INSERT и DELETE; и язык запросов данных (Data Query Language — DQL), который используется для выборки данных из базы. Примером DQL может служить команда SELECT.

Зачастую после выполнения команды результаты представляются не одним значением, а набором результатов или даже коллекцией наборов результатов. Набор результатов (result set) — это просто табличные данные, которые могут содержать одну или несколько таблиц. Набор результатов можно прочитать в Подключенном стиле — с помощью объекта DateReader. Но можно прочитать набор результатов и так: заполнить представление объекта данными и отключиться от источника данных. Будет показано, что для улучшения эффективности пула подключений очень важно открывать подключение как можно 1юзже и закрывать его как можно раньше. А пока достаточно уяснить, что пул подключений (connection pooling) — это термин, относящийся к технике или процессу совместного использования открытого подключения к источнику данных различными запросами для существенного повышения производительности. Большинство поставщиков предоставляют эту возможность по умолчанию; т.е. чтобы воспользоваться преимуществами буферизации подключения, совсем не нужно писать какой-нибудь код, а нужно дашь подчиняться определенным правилам.

Так что нам нужен объект для хранения автономных данных. В силу автономности данных реализация этого объекта не должна зависеть от источника данных, поскольку он играет роль универсального посредника. Другими словами, реализация объекта, хранящего автономные данные, не должна учитывать особенности исходного источника данных, будь то Microsoft SQL Server или Oracle. Этим посредником между подключенным и автономным миром явлиется объект DataAdapter, описанный ниже в данной главе.

Как уже упоминалось, для хранения автономных данных можно написать собственный бизнес-объект. Такой подход, конечно, возможен, но тогда вам почти наверняка придется потрудиться над созданием бизнес-объектов — особенно учитывая то. что теперь вы ответственны за написание всего кода, выполняющего различные возможные Действия: привязка по данным, управление состоянием, история версий строк и т.д. (они более подробно будут рассмотрены в следующих статьях). Однако неочевидно, что можно создать архитектуру на базе бизнес-объектов, которая в длительной перспективе может упростить работу — скорее эта архитектура просто более приспособлена к конкретной ситуации. Различные достоинства и недостатки использования специализированных объектов вместо DataSet изложены в следующих статьях.

Проще всего разобраться в структуре DataSet, проследив его аналогии с СУРБД. Но не забывайте, что Оэ~ аЗе- — это объект, находящийся в памяти. Его не следует путать с СУРБД. Единственным его назначением является то. чего не может обеспечить СУРБД: предоставление реляционных структурированных данных в автономном, переносимом и находящемся в памяти объекте. .

И раз уж DataSet больше всего похож на реляционную базу данных, со всеми таблицами и отношениями между ними с помощью внешних ключей, то класс DataTabie больше всего похож на таблицу, a DataRelation — на ограничение с помощью внешнего ключа. Аналогично класс DataColurr.n больше всего похож на столбец, a DataRow — на строку.

Итак, объект DataSet содержит коллекцию объектов DataTabie в виде свойства Tables типа DacaTableColsection. Кроме того, он содержит свойство Relations типа DataPlaceСоllection которое представляет собой коллекцию объектов DataRelation.

Точно так же объект DataTabie имеет свойство Columns, представляющее собой коллекцию объектов DataColumn в объекте DataColumnCollection- Кроме того, он имеет свойство Rows тина DataRowCoLlection, содержащее различнее строки в виде объектов DataRow.

Объект DataTabie может содержать ограничения, определенные для себя самого (например, UniqueConstraxnt), набор которых хранится в свойстве Constraints типа ConsraintCollection. которое содержит коллекцию объектов типа Constraint либо типа, наследуемого от класса Constraint.

Итак, у нас есть команды, предназначенные для обработки и выборки данных, а также классы для хранения выбранных данных. Теперь мы рассмотрим два способа выборки данных из источника данных.