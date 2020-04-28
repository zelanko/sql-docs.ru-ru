---
title: Аргументы в функциях каталога | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], about arguments
- functions [ODBC], catalog functions
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 819c10d0b137d5e0999c1e10bf22810392509f76
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81288170"
---
# <a name="arguments-in-catalog-functions"></a>Аргументы в функциях каталога
Все функции каталога принимают аргументы, с помощью которых приложение может ограничить область возвращаемых данных. Например, первый и второй вызовы **SQLTables** в следующем коде возвращают результирующий набор, содержащий сведения обо всех таблицах, а третий вызов возвращает сведения о таблице Orders:  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Строковые аргументы функции каталога делятся на четыре разных типа: обычный аргумент (OA), аргумент значения шаблона (ПС), аргумент идентификатора (идентификатор) и аргумент списка значений (Корпоративная лицензия). Большинство строковых аргументов могут иметь один из двух различных типов, в зависимости от значения атрибута инструкции SQL_ATTR_METADATA_ID. В следующей таблице перечислены аргументы для каждой функции каталога и описан тип аргумента для SQL_TRUE или SQL_FALSE значение SQL_ATTR_METADATA_ID.  
  
|Функция|Аргумент|Введите, когда SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|Введите, когда SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA ПС|ИДЕНТИФИКАТОР ID ID ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ИДЕНТИФИКАТОР ID ID ID|  
|**SQLForeignKeys**|*Пккаталогнаме* *пксчеманаме* *PKTableName* *фккаталогнаме* *фксчеманаме* *фктабленаме*|OA OA OA OA OA OA|ИДЕНТИФИКАТОР ID ID ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ID ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* для *CNAME* *ColumnName*|OA PV PV PV|ИДЕНТИФИКАТОР ID ID ID|  
|**SQLProcedures**|*CatalogName* *SchemaName* ( *CNAME* )|OA PV PV|ИДЕНТИФИКАТОР ID ID|  
|**SQLSpecialColumns**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ID ID|  
|**SQLStatistics**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ID ID|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|OA PV PV|ИДЕНТИФИКАТОР ID ID|  
|**SQLTables**|*CatalogName* *SchemaName* *TableName* *TableType*|ПС PV PV КОРПОРАТИВНАЯ ЛИЦЕНЗИЯ|ИДЕНТИФИКАТОР ID — КОРПОРАТИВНАЯ ЛИЦЕНЗИЯ|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обычные аргументы](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Аргументы значения шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Аргументы идентификатора](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Аргументы списка значений](../../../odbc/reference/develop-app/value-list-arguments.md)
