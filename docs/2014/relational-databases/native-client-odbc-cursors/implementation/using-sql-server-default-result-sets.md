---
title: Результирующие наборы по умолчанию SQL Server с помощью | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e4b818f3ec580468a3ae1120709ffaa9c19a8ffe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194482"
---
# <a name="using-sql-server-default-result-sets"></a>Использование результирующих наборов по умолчанию в SQL Server
  Атрибутами курсора ODBC по умолчанию являются:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Каждый раз, когда эти атрибуты имеют значения по умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] результирующий набор по умолчанию. Результирующие наборы по умолчанию могут использоваться для любой инструкции SQL, поддерживаемой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], и являются самым эффективным методом передачи всего результирующего набора клиенту.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] улучшенную поддержку нескольких активных результирующих наборов (MARS); Теперь приложения могут иметь более одного активного результирующего набора в расчете на соединение. По умолчанию режим MARS не включен.  
  
 До версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] принимаемые по умолчанию результирующие наборы не поддерживали несколько активных инструкций для одного соединения. После выполнения инструкции SQL для соединения сервер не принимает команд от клиента в этом соединении до тех пор, пока не будут обработаны все строки результирующего набора. Исключение составляют запросы на отмену оставшейся части результирующего набора. Для отмены оставшейся части частично обработанного результирующего набора, вызовите [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) или [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) с *fOption* параметр должен иметь значение SQL_CLOSE. Чтобы завершить частично обработанного результирующего набора и тестирования на наличие другой результирующий набор, вызовите [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md). Если приложение ODBC пытается выполнить команду над дескриптором соединения до полной обработки результирующего набора по умолчанию, вызов приводит к возникновению ошибки SQL_ERROR и вызов **SQLGetDiagRec** возвращает:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>См. также  
 [Способы реализации курсоров](how-cursors-are-implemented.md)  
  
  