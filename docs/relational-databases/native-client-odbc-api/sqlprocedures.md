---
title: SQLProcedures | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a6f68576d274ac7405045fe13faf15e4c13a0473
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715308"
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Все хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращают какое-либо значение. **SQLProcedures** reports SQL_PT_FUNCTION для PROCEDURE_TYPE столбца результирующего набора.  
  
 **SQLProcedures** возвращает SQL_SUCCESS, существуют ли значения для параметров *CatalogName, SchemaName* или *CNAME* . Функция**SQLFetch** возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 **SQLProcedures** может выполняться на статическом серверном курсоре. Попытка выполнить **SQLProcedures** для обновляемого (динамического или ключевого набора ключей) курсора возвратит SQL_SUCCESS_WITH_INFO, указывая, что тип курсора был изменен.  
  
 **SQLProcedures** возвращает сведения обо всех процедурах, имена которых совпадают с записями *CNAME* и могут быть выполнены текущим пользователем или для которого текущий пользователь предоставил разрешение View definition.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLProcedures](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
