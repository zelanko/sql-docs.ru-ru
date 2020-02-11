---
title: Функции каталога в ODBC | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8cd46fbc8f633ef31f00fa60ced885f9455f185
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68062735"
---
# <a name="catalog-functions-in-odbc"></a>Функции работы с каталогами в ODBC
ODBC содержит следующие функции каталога:  
  
|Компонент|Description|  
|--------------|-----------------|  
|**SQLTables**|Возвращает список каталогов, схем, таблиц или табличных типов в источнике данных.|  
|**SQLColumns**|Возвращает список столбцов в одной или нескольких таблицах.|  
|**SQLStatistics**|Возвращает список статистических данных о одной таблице. Также возвращает список индексов, связанных с этой таблицей.|  
|**SQLSpecialColumns**|Возвращает список столбцов, которые однозначно идентифицируют строку в одной таблице. Также возвращает список столбцов в этой таблице, которые обновляются автоматически.|  
|**SQLPrimaryKeys**|Возвращает список столбцов, составляющих первичный ключ одной таблицы.|  
|**SQLForeignKeys**|Возвращает список внешних ключей в одной таблице или список внешних ключей в других таблицах, ссылающихся на одну таблицу.|  
|**SQLTablePrivileges**|Возвращает список привилегий, связанных с одной или несколькими таблицами.|  
|**SQLColumnPrivileges**|Возвращает список привилегий, связанных с одним или несколькими столбцами в одной таблице.|  
|**SQLProcedures**|Возвращает список процедур в источнике данных.|  
|**SQLProcedureColumns**|Возвращает список входных и выходных параметров, возвращаемое значение и столбцы в результирующем наборе одной процедуры.|  
|**SQLGetTypeInfo**|Возвращает список типов данных SQL, поддерживаемых источником данных. Эти типы данных обычно используются в инструкциях **CREATE TABLE** и **ALTER TABLE** .|  
  
 Поскольку **SQLTables**, **SQLColumns**, **SQLStatistics**и **SQLSpecialColumns** соответствуют интерфейсу командной строки Open Group, а **SQLGetTypeInfo** соответствует интерфейсу командной строки ISO 92, они реализуются большинством драйверов. Остальные функции каталога находятся на уровне соответствия ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Аргументы в функциях каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Представления схемы](../../../odbc/reference/develop-app/schema-views.md)
