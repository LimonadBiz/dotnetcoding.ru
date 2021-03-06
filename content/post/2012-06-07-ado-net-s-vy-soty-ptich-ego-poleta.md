---
title: ADO.NET с высоты птичьего полета
author: dotnetcoding
type: post
date: 2012-06-07T18:44:10+00:00
url: /coding/ado-net-s-vy-soty-ptich-ego-poleta.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
ADO.NET находится в .NET Framework в пространстве имен System. Data. Как и любая другая часть .NET Framework, ADO.NET существует не сама по себе. В System .Windows . Forms. System .Xml, System .Web и других пространствах имен -NET Framework имеются классы, взаимодействующие с ADO.NET<!--more--> для выполнении таких действий, как перетаскивание мышыо. транзакции и т.д. Примером такого класса является Bindir.gSource. находящийся в пространстве имен System .Windows . Forms, который позволяет инкапсулировать источник данных для привязки к данным.

Транзакции будут описываться потом, а создание управляемых данными приложений с помощью перетаскивания мышью будет описано чуть раньше. Перетаскивание мышью в ADO.NET является быстрым и легким способом создания управляемых данными приложений. Оно занимает свое мсето в общей схеме, когда речь идет о создании прототипов или простых приложений при невозможности создания полномасштабной архитектуры уровня предприятия (из-за ограничений на. время или бюджет); однако операции перетаскивания явно не хватает для создания работающих приложений уровня предприятия — в большинстве случаев придется повозиться с реальным кодированием. А для написания эффективного кода абсолютно необходимо разбираться в структуре классов ADO.NET, а также в назначении и поведении каждого конкретного компонента ADO.NET.
  
<a href="http://dotnetcoding.ru/coding/ob-ektnaya-model-ado-net.html" target="_blank">Уже упоминалось</a> еще одно — что различные подключенные части ADO. NET зависят от источника данных. Все подключенные части для конкретного источника данных вместе называются поставщиком данных для этого источника данных. По соглашению поставщики данных достуниы в собственных пространствах имен, входящих в пространство имен System. Data. Например, поставщик данных, позволяющий подключиться к базе данных Oracle, обычно находится в System.Data.OraclеClient, а поставщик данных, позволяющий подключиться к Microsoft SQL Server находится в System.Data.SqlСlient. Но это всего лишь соглашение, так что не удивляйтесь, если встретите поставщик данных, не удовлетворяющий этому соглашению.

На самом деле различные классы и интерфейсы, от которых наследуются или которые реализуют различные классы разнообразных поставщиков данных, могут быть легко реализованы любым сторонним поставщиком данных. И вы сами можете написать свой собственный поставщик данных, просто унаследовав его от нужных классов и реализовав нужные интерфейсы. Понятно, что такой собственно поставщик данных может находиться в любом выбранном вами пространстве имен.

ADO.NET — это архитектура доступа к данным. Такая архитектура должна позволять выполнять несколько самых распространенных действий: устанавливать подключение к источнику данных, выполнять команды, передавать этим командам параметры и выбирать полученные результаты.

Давайте рассмотрим все эти операции по отдельности, чтобы понять, как объекты ADO.NET позволяют их выполнять: <a href="http://dotnetcoding.ru/coding/ustanovlenie-podklyucheniya-disconnection.html" target="_blank">установление подключения: Disconnection</a>.