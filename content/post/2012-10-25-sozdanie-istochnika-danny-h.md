---
title: Создание источника данных
author: dotnetcoding
type: post
date: 2012-10-25T11:27:32+00:00
url: /coding/sozdanie-istochnika-danny-h.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
речь пойдет о работе с автономными данными, так что в идеале пример с автономными данными должен быть достаточно гибким и обобщенным, чтобы служить основой для всех примеров, рассматривающих различные ситуации, с которыми вы можете встретиться в своей программистской практике.
  
<!--more-->


  
Автономные данные, используемые в большинстве примеров данной книги, основаны на простой ситуации потребителей и товаров. Может быть много товаров и может быть много потребителей. Кроме того, между потребителями и товарами имеется отображение “многие ко многим’-, которое содержится еще в одной таблице с именем CustomerProducts.

Зачастую в таких ситуациях создаются ссылки на реализации строго типизированных DataSet, так что может потребоваться создать и строго типизированный DataSet, и базовый DataSet.
  
Кроме того, как уже было сказано, эту структуру данных DataSet можно легко заполнить данными в автономном режиме. Возвратитесь, если вам нужно освежить в памяти, как заполнять подобный DataSet, хотя код заполнения DataSet приведен в листингах. Этот же код пригоден и для заполнения строго типизированного DataSet. Этот код, а также соответствующий Строго типизированный DataSet можно взять с web-сайта издательства. Как видите. вместо программной построчной загрузки DataSet этот код просто читает в DataSet XML-файл.