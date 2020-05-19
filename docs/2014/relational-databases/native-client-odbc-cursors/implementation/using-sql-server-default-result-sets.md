---
title: Использование SQL Server результирующих наборов по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fe9ecf81abe12da2db3e7183fd517e01947c2942
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705644"
---
# <a name="using-sql-server-default-result-sets"></a>Использование результирующих наборов по умолчанию в SQL Server
  Атрибутами курсора ODBC по умолчанию являются:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Если для этих атрибутов заданы значения по умолчанию, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента использует [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] результирующий набор по умолчанию. Результирующие наборы по умолчанию могут использоваться для любой инструкции SQL, поддерживаемой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], и являются самым эффективным методом передачи всего результирующего набора клиенту.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]Добавлена поддержка множественных активных результирующих наборов (MARS). у приложений теперь может быть несколько активных результирующих наборов по умолчанию для каждого подключения. По умолчанию режим MARS не включен.  
  
 До версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] принимаемые по умолчанию результирующие наборы не поддерживали несколько активных инструкций для одного соединения. После выполнения инструкции SQL для соединения сервер не принимает команд от клиента в этом соединении до тех пор, пока не будут обработаны все строки результирующего набора. Исключение составляют запросы на отмену оставшейся части результирующего набора. Чтобы отменить оставшуюся часть частично обработанного результирующего набора, вызовите [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) или [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) , указав для параметра *параметром fOption* значение SQL_CLOSE. Чтобы завершить частично обработанный результирующий набор и проверить наличие другого результирующего набора, вызовите [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md). Если приложение ODBC пытается выполнить команду в обработчике соединения до того, как результирующий набор по умолчанию будет полностью обработан, вызов создает SQL_ERROR и вызов **SQLGetDiagRec** возвращает:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>См. также  
 [Способы реализации курсоров](how-cursors-are-implemented.md)  
  
  
