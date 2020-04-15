---
title: Полей дескриптора Документы Майкрософт
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
ms.openlocfilehash: 94e70de7d237c2eca9aee81979cb19d5295561b5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305925"
---
# <a name="descriptor-fields"></a>Поля дескриптора
Дескрипторы содержат поля *заголовка* и *записи,* полностью описывающие столбцы или параметры.  
  
 Дескриптор содержит одну копию следующих полей заголовка. Изменение поля заголовка влияет на все столбцы или параметры.  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Дескриптор содержит ноль или более записей дескриптора. Каждая запись описывает столбец или параметр, в зависимости от типа дескриптора. При совмещении нового столбца или параметра в дескриптор добавляется новая запись. Когда столбец или параметр не связан, запись удаляется из дескриптора. Каждая запись содержит одну копию следующих полей:  
  
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
  
 Многие атрибуты оператора соответствуют полю заголовка дескриптора. Настройка этих атрибутов с помощью вызова в **S'LSetStmtAttr** и настройка соответствующего поля заголовка дескриптора, позвонив по **s'LSetDesccField,** имеет тот же эффект. То же самое можно сказать и о **S'LGetStmtAttr** и **S'LGetDescField**, оба из которых получают ту же информацию. Вызов функций оператора вместо функций дескриптора имеет то преимущество, что ручка дескриптора не должна быть извлечена.  
  
 Следующие поля заголовка могут быть установлены путем установки атрибутов оператора:  
  
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
