---
title: Дескрипторы и драйверы настольных баз данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], descriptors
- Jet-based ODBC drivers [ODBC], descriptors
- descriptors [ODBC], Jet-supported descriptor fields
- ODBC desktop database drivers [ODBC], descriptors
ms.assetid: 9ae2d9b5-365f-4f0a-9116-defe9498b401
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ef79855f71d23e5a884822371f1894eb83442a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303515"
---
# <a name="descriptors-and-desktop-database-drivers"></a>Дескрипторы и драйверы для баз данных на настольном компьютере
Дескриптор — это структура данных, которая содержит информацию о данных столбца или динамических параметрах. **Для** извлечения поддерживаемых дескрипторов, перечисленных ниже, можно использовать для получения поддерживаемых дескрипторов. Дескрипторы параметров реализации (IPD) не заселены автоматически, так как **S'LDescribeParam** не поддерживается. Не поддерживаются также полей дескриптора, которые недоступны через Jet (например, SQL_DESC_BASE_TABLE_NAME).  
  
 Для получения дополнительной информации о директивных *Microsoft Jet Database Engine Programmer's Guide*полях, поддерживаемых Jet, см.  
  
 Для получения дополнительной информации о дескрипторах, смотрите темы в статье "Описатели" в *справке программиста ODBC*.  
  
|Описатели поля|Уровень поддержки|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Поддерживается|  
|SQL_DESC_ARRAY_SIZE|Поддерживается только для ARD|  
|SQL_DESC_ARRAY_STATUS_PTR|Поддерживается|  
|SQL_DESC_BIND_OFFSET_PTR|Поддерживается|  
|SQL_DESC_BIND_TYPE|Поддерживается|  
|SQL_DESC_COUNT|Поддерживается|  
|SQL_DESC_ROWS_PROCESSED_PTR|Поддерживается только для ARD|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Поддерживается|  
|SQL_DESC_BASE_COLUMN_NAME|Поддерживается (NEW)|  
|SQL_DESC_BASE_TABLE_NAME|Поддерживается (NEW)|  
|SQL_DESC_CASE_SENSITIVE|Всегда FALSE|  
|SQL_DESC_CATALOG_NAME|Не поддерживается|  
|SQL_DESC_CONCISE_TYPE|Поддерживается|  
|SQL_DESC_DATA_PTR|Поддерживается|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Поддерживается|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|Поддерживается для типов INTERVAL C|  
|SQL_DESC_DISPLAY_SIZE|Поддерживается|  
|SQL_DESC_FIXED_PREC_SCALE|Поддерживается (ПРАВДА за деньги)|  
|SQL_DESC_INDICATOR_PTR|Поддерживается|  
|SQL_DESC_LABEL|Поддерживается|  
|SQL_DESC_LENGTH|Поддерживается|  
|SQL_DESC_LITERAL_PREFIX|Поддерживается|  
|SQL_DESC_LITERAL_SUFFIX|Поддерживается|  
|SQL_DESC_LOCAL_TYPE_NAME|Не поддерживается (возвращает строку EMPTY)|  
|SQL_DESC_NAME|Поддерживается|  
|SQL_DESC_NULLABLE|Поддерживается<br /><br /> **Заметка** Не поддерживается в версиях, предшествующих Jet 4.0|  
|SQL_DESC_NUM_PREC_RADIX|Поддерживается|  
|SQL_DESC_OCTET_LENGTH|Поддерживается|  
|SQL_DESC_OCTET_LENGTH_PTR|Поддерживается|  
|SQL_DESC_PARAMETER_TYPE|Только параметры ввода|  
|SQL_DESC_PRECISION|Поддерживается|  
|SQL_DESC_SCALE|Поддерживается|  
|SQL_DESC_SCHEMA_NAME|Не поддерживается|  
|SQL_DESC_SEARCHABLE|Поддерживается|  
|SQL_DESC_TABLE_NAME|Не поддерживается|  
|SQL_DESC_TYPE|Поддерживается|  
|SQL_DESC_TYPE_NAME|Поддерживается|  
|SQL_DESC_UNNAMED|Поддерживается|  
|SQL_DESC_UNSIGNED|Поддерживается|  
|SQL_DESC_UPDATABLE|Поддерживается|
