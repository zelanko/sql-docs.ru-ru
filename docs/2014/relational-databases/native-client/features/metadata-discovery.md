---
title: Обнаружение метаданных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 50455f67760c920881f9f8daaf42d7abe4037c45
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707282"
---
# <a name="metadata-discovery"></a>Обнаружение метаданных
  Улучшение обнаружения метаданных в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] позволяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственным клиентским приложениям гарантировать, что метаданные столбца или параметра, возвращаемые при выполнении запроса, идентичны или совместимы с форматом метаданных, указанным перед выполнением запроса. Если формат метаданных, возвращенных в результате выполнения запроса, будет несовместим с форматом, указанным до выполнения запроса, возвращается ошибка.  
  
 В функциях bcp и ODBC, а также интерфейсах IBCPSession и IBCPSession2 теперь можно задавать отложенное чтение (отложенное обнаружение метаданных), чтобы избежать обнаружения метаданных для операций с параметром queryout. Это позволяет повысить производительность и устранить ошибки обнаружения метаданных.  
  
 Если приложение разрабатывается с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , но соединение с версией сервера, более ранней [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , чем, функция обнаружения метаданных будет соответствовать версии сервера.  
  
## <a name="remarks"></a>Примечания  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие функции bcp, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 При указании формата метаданных с помощью [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)также отображается улучшение производительности.  
  
 [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) имеет новый *eOption* для управления поведением bcp_readfmt: `BCPDELAYREADFMT` .  
  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие функции ODBC, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)  
  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие методы OLE DB, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (дополнительные сведения см. в разделе документации [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md)).  
  
 Повышение производительности также заметно при указании формата метаданных с помощью метода IBCPSession::BCPSetBulkMode.  
  
 Улучшенное обнаружение метаданных в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] стало возможным благодаря добавлению в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] двух хранимых процедур:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](sql-server-native-client-features.md)  
  
  
