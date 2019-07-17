---
title: SQLFreeStmt | Документация Майкрософт
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1623779ba0fb47df1750e72b2e66ff7ad492a3e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135478"
---
# <a name="sqlfreestmt"></a>Функция SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Как правило   
      Не рекомендуется применять функцию**SQLFreeStmt** в ODBC 3.0 и более поздних версиях. Однако если приложению требуется повторно использовать инструкцию следует по-прежнему использовать **SQLFreeStmt** с **SQL_RESET_PARAMS** и **SQL_UNBIND** параметры). Можно также использовать [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), и [ SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) заменить или дублируют функцию **SQLFreeStmt** и вместо него следует использовать их.  
  
 Как правило более эффективным будет повторное использование инструкций, чем их удаление и выделение. Тем не менее в некоторых ситуациях, как повторное использование инструкций, SQLFreeStmt по-прежнему необходимо использовать.  
  
## <a name="see-also"></a>См. также  
 [SQLFreeStmt, функция](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
