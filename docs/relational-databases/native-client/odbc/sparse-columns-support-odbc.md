---
title: Поддержка sparse столбцов (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2dd987453202af2d7761e70193f8a0968f4ad38d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303711"
---
# <a name="sparse-columns-support-odbc"></a>Поддержка разреженных столбцов (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этом разделе описывается поддержка разреженных столбцов драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Для примера, демонстрирующего поддержку ODBC для [Call SQLColumns on a Table with Sparse Columns](../../../relational-databases/native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md)разреженных столбцов, см. Для получения дополнительной информации о разреженной столбцов, см. [Sparse колонки поддержка в S'L Сервер Родной клиент](../../../relational-databases/native-client/features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Метаданные инструкции  
 Поле дескриптора в дескрипторе параметра приложения (APD) и атрибут инструкции SQL_SOPT_SS_NAME_SCOPE принимают дополнительные значения SQL_SS_NAME_SCOPE_EXTENDED и SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Эти значения определяют, какие столбцы включаются в возвращаемый [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)результирующий набор. Дополнительные сведения об атрибуте SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Новый дескриптор строки реализации (IRD), доступное только для чтения поле SQL_CA_SS_IS_COLUMN_SET типа SQLSMALLINT, позволяет определить, имеет ли столбец значение XML **column_set** . SQL_CA_SS_IS_COLUMN_SET принимает значения SQL_TRUE and SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Метаданные каталога  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в результирующий набор для [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>Поддержка функций ODBC для разреженных столбцов  
 Следующие функции ODBC были обновлены для поддержки разреженных столбцов в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
