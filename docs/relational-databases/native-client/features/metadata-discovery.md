---
title: Обнаружение метаданных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d822362e9f9f7e70e4421056383aae8ddef03dc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303365"
---
# <a name="metadata-discovery"></a>Обнаружение метаданных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Улучшение обнаружения метаданных [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяет приложениям Native Client гарантировать, что метаданные столбца или параметра, возвращенные из выполнения запроса, идентичны или совместимы с форматом метаданных, указанным перед выполнением запроса. Если формат метаданных, возвращенных в результате выполнения запроса, будет несовместим с форматом, указанным до выполнения запроса, возвращается ошибка.  
  
 В функциях bcp и ODBC, а также интерфейсах IBCPSession и IBCPSession2 теперь можно задавать отложенное чтение (отложенное обнаружение метаданных), чтобы избежать обнаружения метаданных для операций с параметром queryout. Это позволяет повысить производительность и устранить ошибки обнаружения метаданных.  
  
 Если вы разрабатываете [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] приложение [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] с использованием Native Client, но подключитесь к версии сервера [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]раньше, функция обнаружения метаданных будет соответствовать версии сервера.  
  
## <a name="remarks"></a>Remarks  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие функции bcp, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   [bcp_columns](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 Вы также увидите улучшение производительности при указании формата метаданных с помощью [bcp_setbulkmode.](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)  
  
 [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) имеет новый *eOption* для контроля поведения bcp_readfmt: **BCPDELAYREADFMT**.  
  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие функции ODBC, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../../relational-databases/native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)  
  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие методы OLE DB, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (дополнительные сведения см. в разделе документации [ICommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md)).  
  
 Повышение производительности также заметно при указании формата метаданных с помощью метода IBCPSession::BCPSetBulkMode.  
  
 Улучшенное обнаружение метаданных в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] стало возможным благодаря добавлению в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] двух хранимых процедур:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>См. также:  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
