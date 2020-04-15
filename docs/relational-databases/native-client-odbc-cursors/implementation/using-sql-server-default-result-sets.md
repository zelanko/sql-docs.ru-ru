---
title: С помощью наборов результатов по умолчанию сервера S'L (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 08926660face8061abdf8352d0c4a84ad7e67f8a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305401"
---
# <a name="using-sql-server-default-result-sets"></a>Использование результирующих наборов по умолчанию в SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Атрибутами курсора ODBC по умолчанию являются:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Всякий раз, когда эти атрибуты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливаются по умолчанию, драйвер Native Client ODBC использует набор результатов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по умолчанию. Результирующие наборы по умолчанию могут использоваться для любой инструкции SQL, поддерживаемой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], и являются самым эффективным методом передачи всего результирующего набора клиенту.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]введена поддержка нескольких активных наборов результатов (MARS); приложения теперь могут иметь более одного активного набора результатов по умолчанию в подключении. По умолчанию режим MARS не включен.  
  
 До версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] принимаемые по умолчанию результирующие наборы не поддерживали несколько активных инструкций для одного соединения. После выполнения инструкции SQL для соединения сервер не принимает команд от клиента в этом соединении до тех пор, пока не будут обработаны все строки результирующего набора. Исключение составляют запросы на отмену оставшейся части результирующего набора. Чтобы отменить оставшуюся часть частично обработанного набора результатов, позвоните по [s'LCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) или [S'LFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с параметром *fOption,* установленным для SQL_CLOSE. Чтобы закончить частично обработанный набор результатов и тест на наличие другого набора результатов, позвоните по [телефону S'LMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md). Если приложение ODBC пытается получить команду на ручке соединения до полной обработки набора результатов по умолчанию, вызов генерирует SQL_ERROR и вызов на **s'LGetDiagRec** возвращается:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>См. также:  
 [Способы реализации курсоров](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
