---
title: "SQLTables | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
caps.latest.revision: "38"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 48d54fa7aacd1cfd4994b15ef5626affe0acf482
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sqltables"></a>SQLTables
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLTables может выполняться для статического серверного курсора. Попытка выполнить SQLTables для обновляемого (динамического или набора ключей) курсора возвращает SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 SQLTables сообщает о таблицах из всех баз данных *CatalogName* параметр имеет значение SQL_ALL_CATALOGS, а все остальные параметры содержат значения по умолчанию (указатели NULL).  
  
 Чтобы сообщить о доступных каталогов, схем и типов таблицы, SQLTables особым образом использует пустые строки (указатели байтов нулевой длины). Пустые строки не являются значениями по умолчанию (указатели NULL).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
 SQLTables возвращает сведения обо всех таблицах, имена которых соответствуют *TableName* , принадлежащих текущему пользователю.  
  
## <a name="sqltables-and-table-valued-parameters"></a>Функция SQLTables и возвращающие табличное значение параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLTables возвращает сведения о табличных типов. Значение TABLE_TYPE, возвращаемое для табличного типа в столбце 4 результирующего набора, возвращаемого SQLTables — тип таблицы. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Таблицы, представления и синонимы имеют общее пространство имен, отличающееся от пространства имен табличных типов. Хотя таблица и представление не могут иметь одинаковое имя, в одном каталоге и схеме можно иметь таблицу и табличный тип с одинаковым именем.  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Функция SQLTables](http://go.microsoft.com/fwlink/?LinkId=59374)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
