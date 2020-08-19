---
description: Поля дескриптора
title: Поля дескрипторов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], fields
- header fields [ODBC]
- record fields [ODBC]
ms.assetid: f38623c8-fdd4-4601-b1f0-97c593d31177
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56ca1fa7d558101774d10c8daa530fa32f3f7d21
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476736"
---
# <a name="descriptor-fields"></a>Поля дескриптора
Дескрипторы содержат поля *заголовка* и *записи* , которые полностью описывают столбцы или параметры.  
  
 Дескриптор содержит одну копию следующих полей заголовка. Изменение поля заголовка влияет на все столбцы или параметры.  

:::row:::
    :::column:::
        SQL_DESC_ALLOC_TYPE  
        SQL_DESC_ARRAY_SIZE  
        SQL_DESC_ARRAY_STATUS_PTR  
        SQL_DESC_BIND_OFFSET_PTR  
    :::column-end:::
    :::column:::
        SQL_DESC_BIND_TYPE  
        SQL_DESC_COUNT  
        SQL_DESC_ROWS_PROCESSED_PTR  
    :::column-end:::
:::row-end:::

 Дескриптор содержит ноль или более записей дескриптора. Каждая запись описывает столбец или параметр в зависимости от типа дескриптора. При привязке нового столбца или параметра в дескриптор добавляется новая запись. Если столбец или параметр не привязан, запись удаляется из дескриптора. Каждая запись содержит одну копию следующих полей:  

:::row:::
    :::column:::
        SQL_DESC_AUTO_UNIQUE_VALUE  
        SQL_DESC_BASE_COLUMN_NAME  
        SQL_DESC_BASE_TABLE_NAME  
        SQL_DESC_CASE_SENSITIVE  
        SQL_DESC_CATALOG_NAME  
        SQL_DESC_CONCISE_TYPE  
        SQL_DESC_DATA_PTR  
        SQL_DESC_DATETIME_INTERVAL_CODE  
        SQL_DESC_DATETIME_INTERVAL_PRECISION  
        SQL_DESC_DISPLAY_SIZE  
        SQL_DESC_FIXED_PREC_SCALE  
        SQL_DESC_INDICATOR_PTR  
        SQL_DESC_LABEL  
        SQL_DESC_LENGTH  
        SQL_DESC_LITERAL_PREFIX  
        SQL_DESC_LITERAL_SUFFIX  
    :::column-end:::
    :::column:::
        SQL_DESC_LOCAL_TYPE_NAME  
        SQL_DESC_NAME  
        SQL_DESC_NULLABLE  
        SQL_DESC_OCTET_LENGTH  
        SQL_DESC_OCTET_LENGTH_PTR  
        SQL_DESC_PARAMETER_TYPE  
        SQL_DESC_PRECISION  
        SQL_DESC_SCALE  
        SQL_DESC_SCHEMA_NAME  
        SQL_DESC_SEARCHABLE  
        SQL_DESC_TABLE_NAME  
        SQL_DESC_TYPE  
        SQL_DESC_TYPE_NAME  
        SQL_DESC_UNNAMED  
        SQL_DESC_UNSIGNED  
        SQL_DESC_UPDATABLE  
    :::column-end:::
:::row-end:::

 Многие атрибуты инструкции соответствуют полю заголовка дескриптора. Установка этих атрибутов через вызов **SQLSetStmtAttr** и задание соответствующего поля заголовка дескриптора путем вызова **SQLSetDescField** имеют одинаковый результат. Это справедливо и для **SQLGetStmtAttr** и **SQLGetDescField**, оба из которых получают одни и те же данные. Вызов функций инструкции вместо функций-дескрипторов имеет преимущество, что дескриптор дескриптора не требуется извлекать.  
  
 Следующие поля заголовков можно задать с помощью атрибутов инструкции:  

:::row:::
    :::column:::
        SQL_DESC_ARRAY_SIZE  
        SQL_DESC_ARRAY_STATUS_PTR  
        SQL_DESC_BIND_OFFSET_PTR  
    :::column-end:::
    :::column:::
        SQL_DESC_BIND_TYPE  
        SQL_DESC_ROWS_PROCESSED_PTR  
    :::column-end:::
:::row-end:::

 Этот раздел содержит следующие подразделы.  
  
-   [Число записей](../../../odbc/reference/develop-app/record-count.md)  
  
-   [Связанные записи дескриптора](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [Отложенные поля](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [Проверка согласованности](../../../odbc/reference/develop-app/consistency-check.md)
