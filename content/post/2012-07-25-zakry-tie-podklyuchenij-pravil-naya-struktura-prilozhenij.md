---
title: 'Закрытие подключений: правильная структура приложений'
author: dotnetcoding
type: post
date: 2012-07-25T09:39:37+00:00
url: /coding/zakry-tie-podklyuchenij-pravil-naya-struktura-prilozhenij.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Объект подключения должен реализовывать интерфейс IDispcsabie. По соглашению для выполнения зачистки в каждом объекте используется метод IDisposable. Большинство воспитанных программистов на .NET всегда вызывают метод Dispose, когда это нужно, по и в С#, и в VB.NET имеются конструкции наподобие блока using, которые автоматически вызывают за вас метод Dispose.<!--more-->

Объект подключения ADO.NET не является исключением из этого правила: он использует метод Dispose для освоболсдсния освобожденных ресурсов. Кроме зачистки освобожденных ресурсов, метод Dispose вызывает метод Сlose объекта подключения и готовит его к повторному использованию из пула подключений. А кроме вызова Close, метод Dispose выполняет еще кое-какую работу, которую не выполняет метод Close: он очищает внутренние наборы от различных параметров, например, от строк подключения для объектов подключения, и таким образом позволяет сборщику мусора повторно использовать память, занятую конкретным объектом подключения. Хотя вызов только метода Close возвращает соответствующий объект в пул подключений для его дальнейшего повторного использования.

Одним из наиболее распространенных способов взаимодействия с базой данных является слой доступа к данным. Слой доступа к данным — это ни что иное, как общий набор классов, необходимый всем частям приложения для общения с базой данных. Реализация слоя доступа к данным имеет несколько преимуществ:

• Автор классов доступа к данным обеспечивает максимально быстрое освобождение (а значит, и закрытие) подключений.

• В слой доступа к данным можно включить замеры производительности.

• Если все же в слое доступа к данным имеется утечка подключений {т.е. создание подключений без их закрытия), ее гораздо легче выявить и устранить.

Примером слоя доступа к данным может служить блок приложений доступа к данным (Data Access Application Block), который можно загрузить с web-сайта Microsoft по адресу http://msdn.microsoft.com/library/en-us/dnbda/html/ daab-rm. asp. Может понадобиться небольшая его подгонка под ваше конкретные потребности, но это хорошая отправная точка.

Если вы решите отказаться от его реализации, то внутри или вне слоя доступа к данным необходимо использовать блоки using или конструкции try. . .catch. . . finally, чтобы гарантировать правильное освобождение подключений.

Вот список различий между вызовом метода Close, вызовом метода Dispose и отсутствием такого вызова:

• Вызов метода Close объекта подключения позволяет возвращать соответствующее подключение в пул.

• Вызов метода Dispose объекта подключения устраняет необходимость явного вызова метода Close. Он гарантирует не только возврат в пул соответствующего подключения, но и зачистку выделенных ресурсов сборщиком мусора.

• Отказ от вызова метода Close или Dispose может существенно снизить производительность приложения, доведя размер аула подключений до максимально разрешенного, после чего все будут ожидать появления доступного объекта подключения. Но даже если открытые подключения и выпадают из области видимости модуля, они не будут убраны сборщиком мусора довольно долгое время, т.к. сам объект подключения не занимает слишком много памяти — а единственным критерием запуска сборщика мусора является нехватка памяти.

В общем, метод Dispose является лучшим вариантом, способствуя уборке мусора и ведению пула подключений; вторым вариантом может быть метод Close, который способствует только ведению пула подключений, а отказ от этих методов настолько плох, что его не стоит и рассматривать.