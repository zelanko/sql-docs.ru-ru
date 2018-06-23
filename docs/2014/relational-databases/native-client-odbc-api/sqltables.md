---
title: SQLTables | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b57c9e62115f7e30dccee569fa32a12545dddaac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194249"
---
# <a name="sqltables"></a>SQLTables
  SQLTables может выполняться для статического серверного курсора. Попытка выполнить SQLTables для обновляемого (динамического или набора ключей) курсора возвращает SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 SQLTables сообщает о таблицах из всех баз данных *CatalogName* параметр имеет значение SQL_ALL_CATALOGS, а все остальные параметры содержат значения по умолчанию (указатели NULL).  
  
 Чтобы сообщить о доступных каталогов, схем и типов таблицы, SQLTables особым образом использует пустые строки (указатели байтов нулевой длины). Пустые строки не являются значениями по умолчанию (указатели NULL).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
 SQLTables возвращает сведения обо всех таблицах, имена которых соответствуют *TableName* , принадлежащих текущему пользователю.  
  
## <a name="sqltables-and-table-valued-parameters"></a>Функция SQLTables и возвращающие табличное значение параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLTables возвращает сведения о табличных типов. Значение TABLE_TYPE, возвращаемое для табличного типа в столбце 4 результирующего набора, возвращаемого SQLTables — тип таблицы. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Таблицы, представления и синонимы имеют общее пространство имен, отличающееся от пространства имен табличных типов. Хотя таблица и представление не могут иметь одинаковое имя, в одном каталоге и схеме можно иметь таблицу и табличный тип с одинаковым именем.  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
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
  
  