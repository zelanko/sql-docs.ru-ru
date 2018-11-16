---
title: Служба курсора Майкрософт для OLE DB (ADO компонент службы) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 500a3e38599b0041b036eb148f837afc67260849
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350508"
---
# <a name="microsoft-cursor-service-for-ole-db-overview"></a>Служба курсора Майкрософт для OLE DB Обзор
Служба курсора Майкрософт для OLE DB дополняет поддержки курсорных функций какого поставщиков данных. Таким образом пользователь понимает относительно однообразного функциональные возможности из всех поставщиков данных.

 Служба курсора делает доступными свойства динамического и расширяет поведение определенных методов. Например [оптимизировать](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) динамических свойств включает создание временных индексов для упрощения некоторых операций, таких как [найти](../../../ado/reference/ado-api/find-method-ado.md) метод.

 Служба курсора включает поддержку пакетного обновления во всех случаях. Также эта система симулирует более мощным типов курсора, таких как динамические курсоры, когда поставщик данных можно передавать только меньшими возможностями курсоры, таких как статические курсоры.

## <a name="keyword"></a>Ключевое слово
 Чтобы вызвать этот компонент службы, установите [записей](../../../ado/reference/ado-api/recordset-object-ado.md) или [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**.

```vb
connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient
```

## <a name="dynamic-properties"></a>Динамические свойства
 При вызове службы курсора для OLE DB, добавляются следующие динамические свойства **записей** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции. Полный список **подключения** и **записей** объект динамические свойства, перечисленные в [индекс динамических свойств ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md). Имена связанных свойств OLE DB, где это необходимо, они заключаются в скобки после имени свойства ADO.

 Изменения в некоторые динамические свойства невидимы в базовый источник данных, после вызова службы курсора. Например, установка *время ожидания команды* свойство **записей** будет недоступен для базового поставщика данных.

```vb

Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" & _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).

```

 Если приложению требуется служба курсора, но вам нужно задания динамических свойств базового поставщика, задайте свойства перед вызовом службы курсора. Параметры свойства объекта команды всегда передаются в базовый поставщик данных, независимо от положения курсора. Таким образом можно также использовать объект команды для установки свойств в любое время.

> [!NOTE]
>  Динамическое свойство DBPROP_SERVERDATAONINSERT не поддерживается службой курсора, даже если он поддерживается базового поставщика данных.

|Имя свойства|Описание|
|-------------------|-----------------|
|Автоматическое повторное вычисление (DBPROP_ADC_AUTORECALC)|Для наборов записей, созданных с помощью службы Data Shaping Service, это значение указывает, как часто вычисляются вычисляемые и статистические столбцы. Значение по умолчанию (значение = 1) — чтобы пересчитать всякий раз, когда служба формирования данных определяет, что значения изменились. Если значение равно 0, вычисляемое или статистические столбцы вычисляются только при построении иерархии изначально.|
|Размер пакета (DBPROP_ADC_BATCHSIZE)|Указывает число инструкций update, которые могут быть объединены перед отправкой в хранилище данных. Дополнительные инструкции в пакете, меньше циклов для данных хранилища.|
|Кэш дочерних строк (DBPROP_ADC_CACHECHILDROWS)|Для наборов записей, созданных с помощью служба формирования данных это значение указывает, хранятся ли дочерними наборами записей в кэше для последующего использования.|
|Версия подсистемы курсора (DBPROP_ADC_CEVER)|Указывает версию используемой службы курсора.|
|Поддерживать изменение состояния (DBPROP_ADC_MAINTAINCHANGESTATUS)|Указывает текст команды, используемой для повторной синхронизации одну или несколько строк в нескольких соединение таблиц.|
|[Оптимизация](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Указывает, должен ли быть создан индекс. Если задано значение **True**, авторизует временный создание индексов для улучшения выполнения определенных операций.|
|[Изменить имя](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Указывает имя **записей**. Может быть упоминаемого в текущем или последующих, формирования команды данных.|
|[Команда синхронизации](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Указывает пользовательские командной строки, который используется [Resync](../../../ado/reference/ado-api/resync-method.md) метод при [уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) действует свойство.|
|[Уникальный каталог](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя базы данных, содержащей таблицы, указанной в **уникальной таблицы** свойство.|
|[Уникальной схемы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя владельца таблицы, на которые ссылается **уникальной таблицы** свойство.|
|[Уникальной таблицы](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|Указывает имя одной таблицы в **записей** создан из нескольких таблиц, которые могут быть изменены по операции вставки, обновления или удаления.|
|Обновления условиям (DBPROP_ADC_UPDATECRITERIA)|Указывает, какие поля в **ГДЕ** предложение используются для обработки конфликтов, происходящих во время обновления.|
|[Обновить повторная синхронизация](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) (DBPROP_ADC_UPDATERESYNC)|Указывает ли **Resync** после неявно вызывается метод [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод (и его поведение), когда **уникальной таблицы** действует свойство.|

 Можно также задать или получить динамического свойства, указав его имя в качестве индекса в **свойства** коллекции. Например, получение и вывод текущего значения [оптимизировать](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) динамического свойства, затем установите новое значение, следующим образом:

```vb
Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True
```

## <a name="built-in-property-behavior"></a>Поведение встроенного свойства
 Служба курсора для OLE DB также влияет на поведение некоторых встроенных свойств.

|Имя свойства|Описание|
|-------------------|-----------------|
|[Примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Дополняет типы курсоров, доступных для **записей**.|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Дополняет типы блокировок, доступных для **записей**. Включает пакетные обновления.|
|[Sort](../../../ado/reference/ado-api/sort-property.md)|Указывает один или несколько полей имен, которые **записей** сортируется, а каждое поле сортируется в порядке возрастания или убывания.|

## <a name="method-behavior"></a>Поведение метода
 Служба курсора для OLE DB включает или влияет на поведение [поле](../../../ado/reference/ado-api/field-object.md) объекта [Append](../../../ado/reference/ado-api/append-method-ado.md) метода; и **записей** объекта [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), и [Сохранить](../../../ado/reference/ado-api/save-method.md) методы.
