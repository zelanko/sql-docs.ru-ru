---
title: "Функции ODBC в каталога | Документы Microsoft"
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
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74b86dfd62a12938d18b4aa11a8d0502db50da13
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-functions-in-odbc"></a>Функций каталога ODBC
ODBC содержит следующие функции каталога:  
  
|Функция|Description|  
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
  
-   [Аргументов в функции работы с каталогами](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Представления схемы](../../../odbc/reference/develop-app/schema-views.md)

