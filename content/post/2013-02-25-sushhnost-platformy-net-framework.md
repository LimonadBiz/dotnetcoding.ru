---
title: Сущность платформы NET Framework
author: anatoliy
type: post
date: 2013-02-25T11:22:26+00:00
url: /coding/sushhnost-platformy-net-framework.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование
tags:
  - NET Framework
  - платформа

---
[<img src="http://dotnetcoding.ru/wp-content/uploads/2013/02/75213108.jpg"  style="margin: 4px;" alt="Сущность платформы NET Framework" width="250" height="200" class="alignleft size-full wp-image-1561" />][1]База NET Framework считается одной из элементов платформы Windows. Она позволяет разрабатывать и применять приложения нового поколения.

Цели базы NET Framework:

  1. Генерирование целостной объективно-ориентированной среды программирования, которая допускает разнородные варианты воплощения: код может храниться и функционировать локально, реализовываться локально, а работать через сеть интернет и функционировать удаленно.
<!--more-->

  2. Предоставление пространства выполнения кода, в котором объем конфликтов при раскрытии программного снабжения и управлении вариантами будет сведен к минимуму.
  3. Программное обеспечение безопасности реализации кода в пространстве &#8212; также коде, который разработан неизвестным создателем или автором с частичным доверием.
  4. Обеспечение пространства реализации кода, который позволяет блокировать проблемы, которые связаны с продуктивностью сред на базе интерпретации либо сценариев.
  5. Синтез работы автора в абсолютно разнородных приложениях: как в приложениях операционной системы, так и электронных приложениях.
  6. Применение индустриальных норм во всех сферах обмена сведениями и, как следствие, обеспечение совместимости кода, который разработан в .NET Framework, с остальными программами.

Платформа версии .NET Framework состоит из двух ключевых элементов: пространства CLR и и библиотеки классов самой платформы Framework. Пространство CLR считается основанием платформы .NET Framework. Это определенный агент, который выполняет управление кодом в момент его выполнения, предоставляющий основные службы, которые связаны с такими процессами, как контролирование памяти, удаленными операциями и потоками, в том числе обеспечивающими безопасность вариантов и иными методами контролирующими правильность кода, тем самым гарантируя стабильность и безопасность приложений. Понятие &#171;контролирование кодом&#187; считается для среды CLR ключевым. Код, который разработан для среды, называется управляемым. Любой иной код станет называться неконтролируемым (неуправляемым).

Библиотека классов &#8212; второй ключевой элемент платформы .NET Framework &#8212; считается обширным объектно-ориентированным комплектом вариантов, которые можно применять для создания самых разнородных приложений &#8212; от стандартных и до новейших утилит и сервисов.

 [1]: http://dotnetcoding.ru/wp-content/uploads/2013/02/75213108.jpg