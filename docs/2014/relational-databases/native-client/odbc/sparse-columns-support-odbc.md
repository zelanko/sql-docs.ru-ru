---
title: Поддержка разреженных столбцов (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
author: rothja
ms.author: jroth
ms.openlocfilehash: cd9d22b7de3b078629f275cb648a9fe5fc70c938
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85017339"
---
# <a name="sparse-columns-support-odbc"></a>Поддержка разреженных столбцов (ODBC)
  В этом разделе описывается поддержка разреженных столбцов драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Пример, демонстрирующий поддержку ODBC для разреженных столбцов, см. в разделе [вызов SQLColumns для таблицы с разреженными столбцами](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md). Дополнительные сведения о разреженных столбцах см. [в разделе Поддержка разреженных столбцов в SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Метаданные инструкции  
 Поле дескриптора в дескрипторе параметра приложения (APD) и атрибут инструкции SQL_SOPT_SS_NAME_SCOPE принимают дополнительные значения SQL_SS_NAME_SCOPE_EXTENDED и SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Эти значения определяют, какие столбцы включаются в возвращаемый [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)результирующий набор. Дополнительные сведения об атрибуте SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).  
  
 Новый дескриптор строки реализации (IRD), доступное только для чтения поле SQL_CA_SS_IS_COLUMN_SET типа SQLSMALLINT, позволяет определить, имеет ли столбец значение XML `column_set`. SQL_CA_SS_IS_COLUMN_SET принимает значения SQL_TRUE and SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Метаданные каталога  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в результирующий набор для [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>Поддержка функций ODBC для разреженных столбцов  
 Следующие функции ODBC были обновлены для поддержки разреженных столбцов в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   [SQLColAttribute](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (ODBC)](sql-server-native-client-odbc.md)  
  
  
