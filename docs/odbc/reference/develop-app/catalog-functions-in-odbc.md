---
title: "Функции ODBC в каталога | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e38bcf3158ba294d09d6898b4ab55b6ecbd33b10
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="catalog-functions-in-odbc"></a>Функций каталога ODBC
ODBC содержит следующие функции каталога:  
  
|Компонент|Description|  
|--------------|-----------------|  
|**SQLTables**|Возвращает список каталогов, схем, таблиц или табличных типов в источнике данных.|  
|**SQLColumns**|Возвращает список столбцов в одной или нескольких таблиц.|  
|**SQLStatistics**|Возвращает список статистику по одной таблице. Также возвращает список индексов, связанных с этой таблицей.|  
|**SQLSpecialColumns**|Возвращает список столбцов, который уникально идентифицирует строки в одной таблице. Также возвращает список столбцов в этой таблице, будут автоматически обновлены.|  
|**SQLPrimaryKeys**|Возвращает список столбцов, которые составляют первичный ключ одной таблицы.|  
|**SQLForeignKeys**|Возвращает список внешних ключей в одну таблицу или список внешние ключи в других таблицах, ссылающихся на одну таблицу.|  
|**SQLTablePrivileges**|Возвращает список прав доступа, связанные с одной или нескольких таблиц.|  
|**SQLColumnPrivileges**|Возвращает список прав доступа, связанные с одного или нескольких столбцов в одной таблице.|  
|**SQLProcedures**|Возвращает список процедур в источнике данных.|  
|**SQLProcedureColumns**|Возвращает список входных и выходных параметров, возвращаемое значение и столбцы в результирующем наборе одну процедуру.|  
|**SQLGetTypeInfo**|Возвращает список типов данных SQL поддерживаются источником данных. Эти типы данных, обычно используются в **CREATE TABLE** и **ALTER TABLE** инструкции.|  
  
 Поскольку **SQLTables**, **SQLColumns**, **SQLStatistics**, и **SQLSpecialColumns** откройте группу CLI и **SQLGetTypeInfo** соответствует ISO 92 CLI, они реализуются большинство драйверов. Остальные функции каталога находятся на уровне совместимости ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Аргументы в функциях каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Представления схемы](../../../odbc/reference/develop-app/schema-views.md)
