---
title: "SQLFreeStmt | Документы Microsoft"
ms.custom: 
ms.date: 11/23/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: "35"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a198bb508f07bd16278df4784d4c5705bbdf8f9e
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="sqlfreestmt"></a>Функция SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Обычно   
      Не рекомендуется применять функцию**SQLFreeStmt** в ODBC 3.0 и более поздних версиях. Однако если приложению требуется повторно использовать инструкцию следует по-прежнему использовать **SQLFreeStmt** с **SQL_RESET_PARAMS** и **SQL_UNBIND** параметры). Можно также использовать [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), и [ SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) заменить или дублируют функцию **SQLFreeStmt** и вместо него следует использовать их.  
  
 Как правило является более эффективным будет повторное использование инструкций, чем их удаление и повторное выделение. Однако в некоторых ситуациях, например повторное использование инструкций, SQLFreeStmt по-прежнему должна использоваться.  
  
## <a name="see-also"></a>См. также  
 [SQLFreeStmt, функция](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
