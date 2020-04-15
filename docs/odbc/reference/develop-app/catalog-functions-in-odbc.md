---
title: Функции каталога в ODBC Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6731018b99f2f3043e48ee7c174a08cb9ef71fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306235"
---
# <a name="catalog-functions-in-odbc"></a>Функции работы с каталогами в ODBC
ODBC содержит следующие функции каталога:  
  
|Компонент|Описание|  
|--------------|-----------------|  
|**SQLTables**|Возвращает список каталогов, схем, таблиц или типов таблиц в источнике данных.|  
|**SQLColumns**|Возвращает список столбцов в одной или нескольких таблицах.|  
|**SQLStatistics**|Возвращает список статистических данных об одной таблице. Также возвращается список индексов, связанных с этой таблицей.|  
|**SQLSpecialColumns**|Возвращает список столбцов, который однозначно идентифицирует строку в одной таблице. Также возвращаетсписок столбцов в этой таблице, которые автоматически обновляются.|  
|**SQLPrimaryKeys**|Возвращает список столбцов, которые составляют основной ключ одной таблицы.|  
|**SQLForeignKeys**|Возвращает список иностранных ключей в одной таблице или список иностранных ключей в других таблицах, которые относятся к одной таблице.|  
|**SQLTablePrivileges**|Возвращает список привилегий, связанных с одной или более таблицами.|  
|**SQLColumnPrivileges**|Возвращает список привилегий, связанных с одним или нескольком столбцов, в одной таблице.|  
|**SQLProcedures**|Возвращает список процедур в источник данных.|  
|**SQLProcedureColumns**|Возвращает список входных и выходных параметров, значение возврата и столбцов в наборе результатов одной процедуры.|  
|**SQLGetTypeInfo**|Возвращает список типов данных S'L, поддерживаемых источником данных. Эти типы данных обычно используются в заявлениях **CREATE TABLE** и **ALTER TABLE.**|  
  
 В связи с тем, что **S'LTables,** **S'LColumns,** **S'LStatistics**и **S'LSpecialColumns** соответствуют требованиям Open Group CLI, а **S'LGetTypeInfo** соответствует ISO 92 CLI, они реализуются большинством драйверов. Остальные функции каталога находятся на уровне соответствия ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Аргументы в функциях каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Представления схемы](../../../odbc/reference/develop-app/schema-views.md)
