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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 649c00f1db486dab4a996138be4e26b0e270fbae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106296"
---
# <a name="arguments-in-catalog-functions"></a>Аргументы в функциях каталога
Все функции работы с каталогами принимать аргументы, с которыми приложение можно ограничить объем возвращаемых данных. Например, первый и второй вызовы **SQLTables** в следующем коде возвращает результирующий набор, содержащий сведения обо всех таблицах, а третий вызов возвращает сведения о таблице Orders:  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Строковые аргументы функции каталога делятся на четыре различных типа: обычный аргумент (OA), аргумент значения шаблона (PV), аргумента идентификатора (ID) и аргумент значения списка (Корпоративная лицензия). Большинство строковых аргументов может быть одного из двух различных типов, в зависимости от значения атрибута SQL_ATTR_METADATA_ID инструкции. В следующей таблице перечислены аргументы для каждой функции каталога и описывает тип аргумента для значения SQL_TRUE или SQL_FALSE SQL_ATTR_METADATA_ID.  
  
|Компонент|Аргумент|Время SQL_<br /><br /> ATTR_METADATA_<br /><br /> ИДЕНТИФИКАТОР = SQL_FALSE|Время SQL_<br /><br /> ATTR_METADATA_<br /><br /> ИДЕНТИФИКАТОР = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОРОМ ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОРОМ ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName*  *FKTableName*|OA OA OA OA OA OA|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОРОМ ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОР|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *ProcName* *ColumnName*|OA PV PV PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОРОМ ID|  
|**SQLProcedures**|*CatalogName* *SchemaName* *ProcName*|OA PV PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОР|  
|**SQLSpecialColumns**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОР|  
|**SQLStatistics**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОР|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|OA PV PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОР|  
|**SQLTables**|*CatalogName* *SchemaName* *TableName* *TableType*|КОРПОРАТИВНАЯ ЛИЦЕНЗИЯ PV PV PV|ИДЕНТИФИКАТОР ID ИДЕНТИФИКАТОР-КОРПОРАТИВНАЯ ЛИЦЕНЗИЯ|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обычные аргументы](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Аргументы значения шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Аргументы идентификатора](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Аргументы списка значений](../../../odbc/reference/develop-app/value-list-arguments.md)
