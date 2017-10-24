---
title: "Служба Microsoft курсора для OLE DB (компонент Service ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- providers [ADO], cursor service for OLE DB
- cursor service for OLE DB [ADO]
ms.assetid: 420d0989-7cfb-4c66-a7b5-f4199d13165d
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d7a1f8568b633417196c6c9dda3e8a3615146603
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-cursor-service-for-ole-db-overview"></a>Службы Microsoft курсора OLE DB Обзор
Служба курсора для OLE DB дополняет поддержки курсорных функций поставщиков данных. В результате пользователь понимает относительно однообразного функции из всех поставщиков данных.

 Службы курсора делает доступными динамических свойств и расширяет поведение определенных методов. Например [оптимизировать](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) динамических свойств позволяет создавать временные индексы для упрощения определенных операций, таких как [найти](../../../ado/reference/ado-api/find-method-ado.md) метод.

 Службы курсора включает поддержку пакетного обновления во всех случаях. Также имитирует более производительные типов курсора, таких как динамические курсоры, когда поставщик данных может поддерживать только меньшими возможностями курсоров, такие как статические курсоры.

## <a name="keyword"></a>Ключевое слово
 Чтобы вызвать этот компонент службы, установите [записей](../../../ado/reference/ado-api/recordset-object-ado.md) или [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**.

```
connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient
```

## <a name="dynamic-properties"></a>Динамические свойства
 При вызове службы курсора для OLE DB, добавляются следующие динамические свойства **записей** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции. Полный список **подключения** и **записей** динамических свойств объектов, перечисленных в [индекс динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md). Связанные имена свойств OLE DB, где это применимо, включаются в круглых скобках после имени свойства ADO.

 Изменения для некоторых динамических свойств не отображаются в источнике данных, после был вызван службы курсора. Например, установка *время ожидания команды* свойство **записей** будет недоступен для базового поставщика данных.

```

Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" & _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).

```

 Если приложение требует службы курсора, но необходимо задать динамических свойств для базового поставщика, задайте свойства перед вызовом службы курсора. Параметры свойства объекта команды всегда передаются базовым поставщиком данных вне зависимости от положения курсора. Таким образом можно также использовать объект команды для установки свойств в любое время.

> [!NOTE]
>  Динамическое свойство DBPROP_SERVERDATAONINSERT не поддерживается службой курсора, даже если он поддерживается базового поставщика данных.

|Имя свойства|Description|
|-------------------|-----------------|
|Автоматическое обновление ссылок (DBPROP_ADC_AUTORECALC)|Наборы записей, созданных с помощью службой формирования данных, это значение указывает, как часто вычисляются вычисляемые и статистические столбцы. Значение по умолчанию (значение = 1) — повторного вычисления всякий раз, когда служба формирования данных определяет, что значения изменились. Если значение равно 0, вычисляемые или статистические столбцы только вычисляются при построенных иерархии.|
|Размер пакета (DBPROP_ADC_BATCHSIZE)|Указывает число инструкций update, которые могут быть объединены перед его отправкой в хранилище данных. Дополнительные инструкции в пакете, хранения меньшее число циклов приема-передачи данных.|
|Кэш дочерних строк (DBPROP_ADC_CACHECHILDROWS)|Для набора записей, созданных с помощью службой формирования данных это значение указывает, хранятся ли дочерними наборами записей в кэше для последующего использования.|
|Версия подсистемы курсора (DBPROP_ADC_CEVER)|Указывает версию используемой службы курсора.|
|Сохранить изменение состояния (DBPROP_ADC_MAINTAINCHANGESTATUS)|Показывает, что текст команды, используемой для повторной синхронизации одну или несколько строк в нескольких соединение таблиц.|
|[Оптимизация](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Указывает, должен быть создан индекс. Если задано значение **True**, разрешает создание временных индексов для улучшения выполнения определенных операций.|
|[Изменить имя](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Указывает имя **записей**. Может быть на которые имеются ссылки в текущем или последующих, формирования команды данных.|
|[Команда синхронизации](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Указывает пользовательские командной строки, который используется [Resync](../../../ado/reference/ado-api/resync-method.md) метод при [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) действует свойство.|
|[Уникальный каталог](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя базы данных, содержащей таблицы, указанной в **уникальной таблицы** свойство.|
|[Уникальной схемы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя владельца таблицы, на которые ссылается **уникальной таблицы** свойство.|
|[Уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя одной таблицы в **записей** создан из нескольких таблиц, которые можно изменить путем вставки, обновления или удаления.|
|Обновление критериев (DBPROP_ADC_UPDATECRITERIA)|Указывает, какие поля в **ГДЕ** предложения используются для обработки конфликтов, происходящих во время обновления.|
|[Обновить повторной синхронизации](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) (DBPROP_ADC_UPDATERESYNC)|Указывает ли **Resync** метод неявно вызывается после [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод (и его поведение), когда **уникальной таблицы** действует свойство.|

 Также можно задать или получить динамических свойств, указав его имя в качестве индекса в **свойства** коллекции. Например, get и распечатать текущее значение [оптимизировать](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) динамических свойств установите новое значение, как показано ниже:

```
Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True
```

## <a name="built-in-property-behavior"></a>Поведение встроенного свойства
 Служба курсора для OLE DB также влияет на поведение некоторых встроенных свойств.

|Имя свойства|Description|
|-------------------|-----------------|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Типы курсоров, доступных для дополнения **записей**.|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Дополняет типы блокировок, доступных для **записей**. Включает пакетного обновления.|
|[Sort](../../../ado/reference/ado-api/sort-property.md)|Указывает один или несколько полей имен, **записей** сортируется, а также будет ли каждое поле сортируется в порядке возрастания или убывания.|

## <a name="method-behavior"></a>Поведение методов
 Служба курсора для OLE DB включает или влияет на поведение [поле](../../../ado/reference/ado-api/field-object.md) объекта [Append](../../../ado/reference/ado-api/append-method-ado.md) метода; и **записей** объекта [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), и [Сохранить](../../../ado/reference/ado-api/save-method.md) методы.

