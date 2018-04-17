---
title: Поля дескриптора | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], fields
- header fields [ODBC]
- record fields [ODBC]
ms.assetid: f38623c8-fdd4-4601-b1f0-97c593d31177
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e0124e8f0f48e6d2dc4140f572f674484ceb6d4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="descriptor-fields"></a>Поля дескриптора
Дескрипторы содержат *заголовок* и *записи* поля, которые полностью описать столбцов или параметров.  
  
 Дескриптор содержит следующие поля заголовка по одной копии. Изменение поля заголовка влияет на все столбцы или параметры.  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Дескриптор содержит ноль или более записей дескриптора. Каждая запись описывает столбца или параметра в зависимости от типа дескриптора. Если новый столбец или параметр привязан, новую запись добавлена в дескриптор. Когда отменяется привязка столбца или параметра, запись удаляется из дескриптора. Каждая запись содержит по одной копии следующие поля:  
  
|||  
|-|-|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_DESC_LOCAL_TYPE_NAME|  
|SQL_DESC_BASE_COLUMN_NAME|SQL_DESC_NAME|  
|SQL_DESC_BASE_TABLE_NAME|SQL_DESC_NULLABLE|  
|SQL_DESC_CASE_SENSITIVE|SQL_DESC_OCTET_LENGTH|  
|SQL_DESC_CATALOG_NAME|SQL_DESC_OCTET_LENGTH_PTR|  
|SQL_DESC_CONCISE_TYPE|SQL_DESC_PARAMETER_TYPE|  
|SQL_DESC_DATA_PTR|SQL_DESC_PRECISION|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_DESC_SCALE|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQL_DESC_SCHEMA_NAME|  
|SQL_DESC_DISPLAY_SIZE|SQL_DESC_SEARCHABLE|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_DESC_TABLE_NAME|  
|SQL_DESC_INDICATOR_PTR|SQL_DESC_TYPE|  
|SQL_DESC_LABEL|SQL_DESC_TYPE_NAME|  
|SQL_DESC_LENGTH|SQL_DESC_UNNAMED|  
|SQL_DESC_LITERAL_PREFIX|SQL_DESC_UNSIGNED|  
|SQL_DESC_LITERAL_SUFFIX|SQL_DESC_UPDATABLE|  
  
 Многие инструкции атрибуты соответствуют поле заголовка дескриптора. Установка этих атрибутов посредством вызова **SQLSetStmtAttr** и настройка соответствующее поле заголовка дескриптора путем вызова **SQLSetDescField** действуют одинаково. То же самое справедливо для **SQLGetStmtAttr** и **SQLGetDescField**, оба способа получить те же сведения. Вызов функций инструкции вместо функции дескриптор преимущество дескриптора, у которого нет требуется получить.  
  
 Можно задать следующие поля заголовка, задав атрибуты инструкции.  
  
|||  
|-|-|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Число записей](../../../odbc/reference/develop-app/record-count.md)  
  
-   [Связанные записи дескриптора](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [Отложенные поля](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [Проверка согласованности](../../../odbc/reference/develop-app/consistency-check.md)
