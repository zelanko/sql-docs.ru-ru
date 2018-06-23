---
title: Поддержка разреженных столбцов (ODBC) | Документы Microsoft
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
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b294c0b1226722f98a14f1f49aeb077216a18d2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191946"
---
# <a name="sparse-columns-support-odbc"></a>Поддержка разреженных столбцов (ODBC)
  В этом разделе описывается поддержка разреженных столбцов драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Пример, демонстрирующий поддержку ODBC для разреженных столбцов см. в разделе [вызов SQLColumns для таблицы с разреженными столбцами](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md). Дополнительные сведения о разреженных столбцах см. в разделе [Поддержка разреженных столбцов в собственном клиенте SQL Server](../features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Метаданные инструкции  
 Поле дескриптора в дескрипторе параметра приложения (APD) и атрибут инструкции SQL_SOPT_SS_NAME_SCOPE принимают дополнительные значения SQL_SS_NAME_SCOPE_EXTENDED и SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Эти значения определяют, какие столбцы включаются в результирующий набор, возвращенный [SQLColumns](../../native-client-odbc-api/sqlcolumns.md). Дополнительные сведения о SQL_SOPT_SS_NAME_SCOPE см. в разделе [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).  
  
 Новый дескриптор строки реализации (IRD), доступное только для чтения поле SQL_CA_SS_IS_COLUMN_SET типа SQLSMALLINT, позволяет определить, имеет ли столбец значение XML `column_set`. SQL_CA_SS_IS_COLUMN_SET принимает значения SQL_TRUE and SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Метаданные каталога  
 Два [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] были добавлены в результирующий набор для определенных столбцов (SS_IS_SPARSE и SS_IS_COLUMN_SET) [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>Поддержка функций ODBC для разреженных столбцов  
 Следующие функции ODBC были обновлены для поддержки разреженных столбцов в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   [SQLColAttribute](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](sql-server-native-client-odbc.md)  
  
  