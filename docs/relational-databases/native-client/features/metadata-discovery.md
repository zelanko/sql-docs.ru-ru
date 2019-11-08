---
title: Обнаружение метаданных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 380d76fe0740a6c43584a68f9353d85539867fe3
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761398"
---
# <a name="metadata-discovery"></a>Обнаружение метаданных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Улучшение обнаружения метаданных в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] позволяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственным клиентским приложениям гарантировать, что метаданные столбца или параметра, возвращаемые при выполнении запроса, идентичны или совместимы с форматом метаданных, который вы указали перед выполнением запрос. Если формат метаданных, возвращенных в результате выполнения запроса, будет несовместим с форматом, указанным до выполнения запроса, возвращается ошибка.  
  
 В функциях bcp и ODBC, а также интерфейсах IBCPSession и IBCPSession2 теперь можно задавать отложенное чтение (отложенное обнаружение метаданных), чтобы избежать обнаружения метаданных для операций с параметром queryout. Это позволяет повысить производительность и устранить ошибки обнаружения метаданных.  
  
 Если приложение разрабатывается с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] но подключается к серверной версии, более ранней, чем [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], функция обнаружения метаданных будет соответствовать версии сервера.  
  
## <a name="remarks"></a>Замечания  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие функции bcp, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   [bcp_columns](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 При указании формата метаданных с помощью [bcp_setbulkmode](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)также отображается улучшение производительности.  
  
 [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) имеет новый *eOption* для управления поведением bcp_readfmt: **BCPDELAYREADFMT**.  
  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие функции ODBC, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../../relational-databases/native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)  
  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] были изменены следующие методы OLE DB, которые теперь обеспечивают улучшенное обнаружение метаданных:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters:: GetParameterInfo (Дополнительные сведения см. в [ICommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md) )  
  
 Повышение производительности также заметно при указании формата метаданных с помощью метода IBCPSession::BCPSetBulkMode.  
  
 Улучшенное обнаружение метаданных в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] стало возможным благодаря добавлению в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] двух хранимых процедур:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>См. также раздел  
 [Компоненты SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
