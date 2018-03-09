---
title: "SQLPrimaryKeys | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 471b21b88cea924970a6c168c0e1c48262325374
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Таблица может содержать столбец или столбцы, которые могут служить уникальными идентификаторами строк и таблицы, созданные без ограничения PRIMARY KEY возвращает пустой результирующий набор для SQLPrimaryKeys. Функция ODBC [SQLSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md) отчеты строк идентификатор кандидатами для таблицы без первичных ключей.  
  
 SQLPrimaryKeys возвращает SQL_SUCCESS независимо от наличия значения существуют для *CatalogName*, *SchemaName*, или *TableName* параметров. SQLFetch возвращает значение SQL_NO_DATA, если в этих параметров используются недопустимые значения.  
  
 SQLPrimaryKeys может выполняться для статического серверного курсора. Попытка выполнить SQLPrimaryKeys для обновляемого (динамического или набора ключей) курсора возвращает SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>Функция SQLPrimaryKeys и возвращающие табличные значения параметры  
 Если атрибут инструкции SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение по умолчанию SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys возвращает сведения о первичных ключевых столбцов для табличных типов. Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLPrimaryKeys](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
