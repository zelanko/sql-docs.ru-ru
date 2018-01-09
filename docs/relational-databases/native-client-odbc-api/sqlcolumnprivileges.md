---
title: "SQLColumnPrivileges | Документы Microsoft"
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
helpviewer_keywords: SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c0ba970bd62ab324e014277c884b8b842e99acdb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLColumnPrivileges** возвращает SQL_SUCCESS независимо от наличия значения существуют для*CatalogName*, *SchemaName*, *TableName*, или  *ColumnName* параметров. Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 **SQLColumnPrivileges** может быть выполнена для статического серверного курсора. Попытка выполнить **SQLColumnPrivileges** для обновляемого (динамического или набора ключей) курсора будет возвращено значение SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента поддерживает выдачу сведений о таблицах на связанных серверах, принимая двухкомпонентное имя *CatalogName* параметр: *имя_связанного_сервера.имя_каталога*.  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLColumnPrivileges](http://go.microsoft.com/fwlink/?LinkId=59335)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
