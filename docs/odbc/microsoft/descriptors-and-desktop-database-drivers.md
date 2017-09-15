---
title: "Дескрипторы и системной базы данных драйверы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- desktop database drivers [ODBC], descriptors
- Jet-based ODBC drivers [ODBC], descriptors
- descriptors [ODBC], Jet-supported descriptor fields
- ODBC desktop database drivers [ODBC], descriptors
ms.assetid: 9ae2d9b5-365f-4f0a-9116-defe9498b401
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 67f656acd349419d7fc3d1c264985beeb36298ce
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="descriptors-and-desktop-database-drivers"></a>Дескрипторы и драйверы для настольных баз данных
Дескриптор является структурой данных, который содержит сведения о данных столбца или динамических параметров. **SQLGetDescField** может использоваться для получения поддерживаемой дескрипторы, перечисленные ниже. Дескрипторов параметра реализации (IPD) не заполняется автоматически из-за **SQLDescribeParam** не поддерживается. Поля дескриптора, которые недоступны через Jet (например, SQL_DESC_BASE_TABLE_NAME) также не поддерживаются.  
  
 Дополнительные сведения о полях дескриптора поддерживается Jet см. в разделе *Microsoft Jet базы данных подсистемы Руководство программиста*.  
  
 Дополнительные сведения о дескрипторах см. в разделах, в разделе «Дескрипторы» в *справочнике программиста ODBC*.  
  
|Поля дескриптора|Уровень поддержки|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Поддерживается|  
|SQL_DESC_ARRAY_SIZE|Поддерживается только для Отменить|  
|SQL_DESC_ARRAY_STATUS_PTR|Поддерживается|  
|SQL_DESC_BIND_OFFSET_PTR|Поддерживается|  
|SQL_DESC_BIND_TYPE|Поддерживается|  
|SQL_DESC_COUNT|Поддерживается|  
|SQL_DESC_ROWS_PROCESSED_PTR|Поддерживается только для Отменить|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Поддерживается|  
|SQL_DESC_BASE_COLUMN_NAME|Поддерживается (новая)|  
|SQL_DESC_BASE_TABLE_NAME|Поддерживается (новая)|  
|SQL_DESC_CASE_SENSITIVE|Всегда имеет значение FALSE|  
|SQL_DESC_CATALOG_NAME|Не поддерживается|  
|SQL_DESC_CONCISE_TYPE|Поддерживается|  
|SQL_DESC_DATA_PTR|Поддерживается|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Поддерживается|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|Поддерживается для типов C ИНТЕРВАЛ|  
|SQL_DESC_DISPLAY_SIZE|Поддерживается|  
|SQL_DESC_FIXED_PREC_SCALE|Поддерживаемые (значение TRUE для money)|  
|SQL_DESC_INDICATOR_PTR|Поддерживается|  
|SQL_DESC_LABEL|Поддерживается|  
|SQL_DESC_LENGTH|Поддерживается|  
|SQL_DESC_LITERAL_PREFIX|Поддерживается|  
|SQL_DESC_LITERAL_SUFFIX|Поддерживается|  
|SQL_DESC_LOCAL_TYPE_NAME|Не поддерживается (возвращает ПУСТУЮ строку)|  
|SQL_DESC_NAME|Поддерживается|  
|SQL_DESC_NULLABLE|Поддерживается<br /><br /> **Примечание** не поддерживается в версиях, предшествующих Jet 4.0|  
|SQL_DESC_NUM_PREC_RADIX|Поддерживается|  
|SQL_DESC_OCTET_LENGTH|Поддерживается|  
|SQL_DESC_OCTET_LENGTH_PTR|Поддерживается|  
|SQL_DESC_PARAMETER_TYPE|Только входные параметры|  
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
