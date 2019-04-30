---
title: Функции ODBC в работы с каталогами | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 84c870d45cc487fc9ec5497e43b764bd4187d2f6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63217619"
---
# <a name="catalog-functions-in-odbc"></a>Функции работы с каталогами в ODBC
ODBC содержит следующие функции каталога:  
  
|Компонент|Описание|  
|--------------|-----------------|  
|**SQLTables**|Возвращает список каталогов, схем, таблиц или табличных типов в источнике данных.|  
|**SQLColumns**|Возвращает список столбцов в одной или нескольких таблиц.|  
|**SQLStatistics**|Возвращает список статистику по одной таблице. Также возвращает список индексов, связанных с этой таблицей.|  
|**SQLSpecialColumns**|Возвращает список столбцов, который однозначно определяет строку в одной таблице. Также возвращает список столбцов в таблице, которая автоматически обновляются.|  
|**SQLPrimaryKeys**|Возвращает список столбцов, составляющих первичный ключ одной таблицы.|  
|**SQLForeignKeys**|Возвращает список внешних ключей в одну таблицу или список внешних ключей в других таблицах, которые ссылаются на одну таблицу.|  
|**SQLTablePrivileges**|Возвращает список прав доступа, связанные с одной или нескольких таблиц.|  
|**SQLColumnPrivileges**|Возвращает список прав доступа, связанные с одного или нескольких столбцов в одной таблице.|  
|**SQLProcedures**|Возвращает список процедур в источнике данных.|  
|**SQLProcedureColumns**|Возвращает список входных и выходных параметров, возвращаемое значение и столбцы в результирующем наборе одну процедуру.|  
|**SQLGetTypeInfo**|Возвращает список типов данных SQL, поддерживаемых источником данных. Эти типы данных, обычно используются в **CREATE TABLE** и **ALTER TABLE** инструкций.|  
  
 Так как **SQLTables**, **SQLColumns**, **SQLStatistics**, и **SQLSpecialColumns** соответствуют интерфейса командной строки откройте группу, а также **SQLGetTypeInfo** соответствует ISO 92 CLI, они реализуются большинство драйверов. Остальные функции каталога размещаются на уровне совместимости ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [Аргументы в функциях каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [Представления схемы](../../../odbc/reference/develop-app/schema-views.md)
