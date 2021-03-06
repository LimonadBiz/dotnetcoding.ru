---
title: Создание типизированных DataSet в Visual Studio .NET
author: dotnetcoding
type: post
date: 2012-07-25T10:55:59+00:00
url: /coding/sozdanie-tipizirovanny-h-dataset-v-visual-studio-net.html
robotsmeta:
  - index,follow
categories:
  - .NET Программирование

---
Visual Studio .NET предоставляет невероятно легкий способ создания строго типизированных DataSet по принципу &#171;укажи и щелкни&#187;. Это настолько органичное расширение Visual Studio .NET, что нет никаких разумных причин не использовать его для разработки приложений. <!--more-->Для начала воспользуемся концепцией из примера “книг и рецензий&#187; и разработаем для нее в Visual Studio .NET строго типизированные DataSet:

1. Начните, как обычно, с создания нового консольного приложения, которое на этот раз называется уже Example 6.7.

2. Теперь щелкните правой кнопкой на имени проекта, выберите пункт Addc-Add Hew Item (Добавить^ Добавить новый элемент), а затем выберите значок DataSet и введите в поле его имени BookDataSet.xsd.

3. Перетащите с палитры инструментов на пустое место в окне конструктора два элемента DataTable. С этого момента можно пользоваться визуальным интерфейсом, чтобы добавить столбцы для каждого находящегося в окне DataTable.

4. Создайте столбцы в соответствии со столбцами, которые были в примере(Books и BookReviews).

5. И в завершение создайте первичный ключ с именем KeyBooklD для столбца BooklD таблицы Books.

6. У пас имеются две полностью обособленные и не связанные между собой таблицы. А теперь переходим к десерту: отношение. Перетащите из палитры инструментов в окно конструктора элемент Relation, протаскивая его над какими-нибудь элементами (или пустым пространством) элемента BookReviews (таблица). Когда вы отпустите кнопку, появится диалог, в котором будет предложено ввести дополнительную информацию об отношении (keyref). Измените имя keyref на KevBooklDRef. Поскольку в одной из таблиц уже есть ключ и в обеих таблицах имеются столбцы с одинаковыми именами, диалог заполняется всей информацией, необходимой для формирования родительского отношения. После закрытия диалогового окна будет сгенерирован соответствующий код.