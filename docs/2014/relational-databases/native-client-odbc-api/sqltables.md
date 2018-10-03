---
title: SQLTables | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90ae76e10c4f9ceab4f7185de6448f6add944b5f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111495"
---
# <a name="sqltables"></a>SQLTables
  SQLTables могут быть выполнены для статического серверного курсора. При попытке выполнить SQLTables для обновляемого (динамического или набора ключей) курсора возвращает SQL_SUCCESS_WITH_INFO, определяющий, что тип курсора был изменен.  
  
 SQLTables о таблицах из всех баз данных, когда *CatalogName* параметр имеет значение SQL_ALL_CATALOGS, а все остальные параметры содержат значения по умолчанию (указатели NULL).  
  
 Чтобы сообщить о доступных каталогов, схемы и табличные типы, SQLTables делает специальное использование пустых строк (указатели байтов нулевой длины). Пустые строки не являются значениями по умолчанию (указатели NULL).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя для *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
 SQLTables возвращает сведения обо всех таблицах, имена которых соответствуют параметру *TableName* и которые принадлежат текущему пользователю.  
  
## <a name="sqltables-and-table-valued-parameters"></a>Функция SQLTables и возвращающие табличное значение параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLTables возвращает сведения о табличных типов. Значение TABLE_TYPE, возвращаемое для табличного типа в столбце 4 результирующего набора, возвращаемого SQLTables является ТАБЛИЧНЫМ ТИПОМ. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Таблицы, представления и синонимы имеют общее пространство имен, отличающееся от пространства имен табличных типов. Хотя таблица и представление не могут иметь одинаковое имя, в одном каталоге и схеме можно иметь таблицу и табличный тип с одинаковым именем.  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="example"></a>Пример  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>См. также  
 [Функция SQLTables](http://go.microsoft.com/fwlink/?LinkId=59374)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
