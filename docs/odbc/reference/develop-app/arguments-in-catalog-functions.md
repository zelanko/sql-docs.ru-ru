---
title: Аргументы в каталоге Функции (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288170"
---
# <a name="arguments-in-catalog-functions"></a>Аргументы в функциях каталога
Все функции каталога принимают аргументы, с помощью которых приложение может ограничить область возвращенных данных. Например, первый и второй вызовы на **S'LTables** в следующем коде возвращают набор результатов, содержащий информацию обо всех таблицах, в то время как третий вызов возвращает информацию о таблице заказов:  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Аргументы строки функции каталога делятся на четыре различных типа: обычный аргумент (OA), аргумент значения шаблона (PV), аргумент идентификатора (ID) и аргумент списка значений (VL). Большинство аргументов строки могут быть одного из двух различных типов, в зависимости от значения атрибута SQL_ATTR_METADATA_ID оператора. В следующей таблице перечислены аргументы для каждой функции каталога и описывается тип аргумента для SQL_TRUE или SQL_FALSE значения SQL_ATTR_METADATA_ID.  
  
|Компонент|Аргумент|Введите, когда SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID и SQL_FALSE|Введите, когда SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID и SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*КаталогНаимя* *СхемаИмя* *ТаблицаИмя* *ColumnName*|ОА ОА.|ID ID ID ID|  
|**SQLColumns**|*КаталогНаимя* *СхемаИмя* *ТаблицаИмя* *ColumnName*|ОА.....|ID ID ID ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName* *FKTableName*|ОА ОА ОА ОА ОА|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*КаталогНаимя* *СхемаНаймЕй* *ТаблицаНай*|ОА ОА|ID ID ID|  
|**SQLProcedureColumns**|*КаталогНаимя* *СхемаНамиг* *ProcName* *ColumnName*|ОА.....|ID ID ID ID|  
|**SQLProcedures**|*КаталогНаимя* *СхемаНамик* *ПрокНаме*|ОА...|ID ID ID|  
|**SQLSpecialColumns**|*КаталогНаимя* *СхемаНаймЕй* *ТаблицаНай*|ОА ОА|ID ID ID|  
|**SQLStatistics**|*КаталогНаимя* *СхемаНаймЕй* *ТаблицаНай*|ОА ОА|ID ID ID|  
|**SQLTablePrivileges**|*КаталогНаимя* *СхемаНаймЕй* *ТаблицаНай*|ОА...|ID ID ID|  
|**SQLTables**|*КаталогИмя* *SchemaName* *ТаблицаНазвание* *ТаблицаТип*|.... VL|ID ID ID VL|  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обычные аргументы](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Аргументы значения шаблона](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Аргументы идентификатора](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Аргументы списка значений](../../../odbc/reference/develop-app/value-list-arguments.md)
