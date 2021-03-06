---
title: Применение XML для работы с автономными данными
author: dotnetcoding
type: post
date: 2013-02-01T11:50:00+00:00
url: /coding/primenenie-xml-dlya-raboty-s-avtonomny-mi-danny-mi.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Объекты DataSet и DataTable — хорошие друзья XML. мы уже рассмотрели одно из удобных свойств объектов, которые могут хранить автономные данные: они хорошо совместимы с XML. <!--more-->И в самом деле, и DataSet, и DataTable допускают легкое преобразование в XML и обратно. Частично вы уже знакомы с этой возможностью в виде методов ReadXml. WnteXml. ReadXrnlSchema. WriteXmlSchema и GetXml (только для DataSet) этих классов. В сущности, данные для всех примеров этой главы хранятся в XML-файле, и мы просто читаем их с помощью метода ReadXml.

Но в классе DataSet есть еще один пока не рассмотренный интересный метод— inferXmlSchema. В промышленных приложениях этот метод лучше не применять: он просматривает все значения в DataSet и возвращает схему, которая по его мнению соответствует этим данным. Для максимальной совместимости метод InferXmlSchema считает, что все столбцы являются строковыми, так что вы не только не получите нужную схему, но это и довольно неэффективный способ генерации схем. Лучше указывать свои собственные схемы. При невозможности указать свою собственную схему лучше уж использовать метод FillSchema, но в приложениях с высокими запросами в режиме промышленной эксплуатации нежелательно пользоваться этим методом напрямую. Лучше подготовить набор схем, готовых для чтения в соответствующие DataSet.
  
Кроме того, вы уже видели, как свойство вложенности объекта DataRelation влияет на генерацию XML этими методами.

Возможности работы в ADO.NET с XML-данными будут гораздо подробнее рассмотрены , но здесь мы все-таки рассмотрим один класс из .NET Framework, позволяющей работать конкретно с автономными данными и XML — класс Xm3DataDocument.