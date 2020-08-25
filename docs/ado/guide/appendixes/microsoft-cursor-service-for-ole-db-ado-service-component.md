---
description: Служба курсора Майкрософт для OLE DB (компонент службы ADO)
title: Служба курсора Майкрософт для OLE DB (компонент службы ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], cursor service for OLE DB
- cursor service for OLE DB [ADO]
ms.assetid: 420d0989-7cfb-4c66-a7b5-f4199d13165d
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e1f1e1ecfef6725cfb15640486d7aeb63e348af
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806594"
---
# <a name="microsoft-cursor-service-for-ole-db-overview"></a>Обзор службы курсоров Майкрософт для OLE DB
Служба курсора Майкрософт для OLE DB дополняет функции поддержки курсоров поставщиками данных. В результате пользователь воспринимает относительно единую функциональность всех поставщиков данных.

 Служба курсора делает динамические свойства доступными и улучшает поведение определенных методов. Например, динамическое свойство [optimize](../../reference/ado-api/optimize-property-dynamic-ado.md) позволяет создавать временные индексы для упрощения определенных операций, таких как метод [Find](../../reference/ado-api/find-method-ado.md) .

 Служба курсоров включает поддержку пакетного обновления во всех случаях. Он также имитирует более производительные типы курсоров, такие как динамические курсоры, когда поставщик данных может предоставлять только менее производительные курсоры, например статические курсоры.

## <a name="keyword"></a>Ключевое слово
 Чтобы вызвать этот компонент службы, задайте для свойства [CursorLocation](../../reference/ado-api/cursorlocation-property-ado.md) [набора записей](../../reference/ado-api/recordset-object-ado.md) или объекта [соединения](../../reference/ado-api/connection-object-ado.md) значение **адусеклиент**.

```vb
connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient
```

## <a name="dynamic-properties"></a>Динамические свойства
 При вызове службы курсора для OLE DB в коллекцию [свойств](../../reference/ado-api/properties-collection-ado.md) объекта **набора записей** добавляются следующие динамические свойства. Полный список динамических свойств **соединения** и объекта **набора записей** содержится в [индексе динамического свойства ADO](../../reference/ado-api/ado-dynamic-property-index.md). Связанные OLE DB имена свойств, где это необходимо, включаются в круглые скобки после имени свойства ADO.

 Изменения некоторых динамических свойств не видны базовому источнику данных после вызова службы курсора. Например, установка свойства *времени ожидания команды* в **наборе записей** не будет видна базовому поставщику данных.

```vb

Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" & _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).

```

 Если приложению требуется служба курсора, но необходимо задать динамические свойства базового поставщика, задайте свойства перед вызовом службы курсора. Параметры свойства объекта команды всегда передаются в базовый поставщик данных независимо от расположения курсора. Таким образом, можно также использовать объект Command для задания свойств в любое время.

> [!NOTE]
>  Динамическое свойство DBPROP_SERVERDATAONINSERT не поддерживается службой курсора, даже если оно поддерживается базовым поставщиком данных.

|Имя свойства|Описание|
|-------------------|-----------------|
|Автоматическое перерасчет (DBPROP_ADC_AUTORECALC)|Для наборов записей, созданных с помощью службы формирования данных, это значение указывает, как часто рассчитываются вычисляемые и статистические столбцы. Значение по умолчанию (Value = 1) — повторное вычисление, когда служба формирования данных определит, что значения были изменены. Если значение равно 0, то вычисляемые или статистические столбцы вычисляются только при первоначальном построении иерархии.|
|Размер пакета (DBPROP_ADC_BATCHSIZE)|Указывает количество инструкций UPDATE, которые могут быть пакетированы перед отправкой в хранилище данных. Чем больше инструкций в пакете, тем меньше обращений к хранилищу данных.|
|Дочерние строки кэша (DBPROP_ADC_CACHECHILDROWS)|Для наборов записей, созданных с помощью службы формирования данных, это значение указывает, хранятся ли дочерние наборы записей в кэше для последующего использования.|
|Версия обработчика курсоров (DBPROP_ADC_CEVER)|Указывает версию используемой службы курсора.|
|Ведение состояния изменений (DBPROP_ADC_MAINTAINCHANGESTATUS)|Указывает текст команды, используемой для повторной синхронизации одной или нескольких строк в соединении нескольких таблиц.|
|[Optimize](../../reference/ado-api/optimize-property-dynamic-ado.md) (Оптимизация)|Указывает, должен ли быть создан индекс. Если задано значение **true**, разрешает временное создание индексов для улучшения выполнения определенных операций.|
|[Изменить имя формы](../../reference/ado-api/reshape-name-property-dynamic-ado.md)|Указывает имя **набора записей**. Можно ссылаться в текущих или последующих командах формирования данных.|
|[Команда повторной синхронизации](../../reference/ado-api/resync-command-property-dynamic-ado.md)|Указывает пользовательскую командную строку, которая используется методом повторной [синхронизации](../../reference/ado-api/resync-method.md) , когда действует свойство [уникальной таблицы](../../reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) .|
|[Уникальный каталог](../../reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя базы данных, содержащей таблицу, на которую ссылается свойство **уникальной таблицы** .|
|[Уникальная схема](../../reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя владельца таблицы, на которую ссылается свойство **уникальной таблицы** .|
|[уникальная таблица](../../reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя таблицы в **наборе записей** , созданном из нескольких таблиц, которые могут быть изменены операциями вставки, обновления или удаления.|
|Критерии обновления (DBPROP_ADC_UPDATECRITERIA)|Указывает, какие поля в предложении **WHERE** используются для обработки конфликтов, происходящих во время обновления.|
|[Повторная синхронизация обновления](../../reference/ado-api/update-resync-property-dynamic-ado.md) (DBPROP_ADC_UPDATERESYNC)|Указывает, вызывается ли метод **Resync** неявно после метода [UpdateBatch](../../reference/ado-api/updatebatch-method.md) (и его поведения), когда действует свойство **уникальной таблицы** .|

 Можно также задать или получить динамическое свойство, указав его имя в качестве индекса для коллекции **свойств** . Например, можно получить и напечатать текущее значение динамического свойства [optimize](../../reference/ado-api/optimize-property-dynamic-ado.md) , а затем задать новое значение следующим образом:

```vb
Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True
```

## <a name="built-in-property-behavior"></a>Поведение встроенного свойства
 Служба курсора для OLE DB также влияет на поведение определенных встроенных свойств.

|Имя свойства|Описание|
|-------------------|-----------------|
|[Примеры CursorType](../../reference/ado-api/cursortype-property-ado.md)|Дополняет типы курсоров, доступные для **набора записей**.|
|[LockType](../../reference/ado-api/locktype-property-ado.md)|Дополняет типы блокировок, доступные для **набора записей**. Включает пакетные обновления.|
|[Sort](../../reference/ado-api/sort-property.md)|Указывает одно или несколько имен полей, по которым сортируется **набор записей** , а также сведения о том, сортируются ли каждое поле в порядке возрастания или убывания.|

## <a name="method-behavior"></a>Поведение метода
 Служба курсора для OLE DB включает или влияет на поведение метода [append](../../reference/ado-api/append-method-ado.md) объекта [field](../../reference/ado-api/field-object.md) . и методы [открытия](../../reference/ado-api/open-method-ado-recordset.md), [ресинхронизации](../../reference/ado-api/resync-method.md), [UpdateBatch](../../reference/ado-api/updatebatch-method.md)и [сохранения](../../reference/ado-api/save-method.md) объекта **Recordset** .