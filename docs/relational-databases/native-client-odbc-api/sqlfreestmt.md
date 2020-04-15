---
title: СЗЛФриСтмт Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3eb86f9b7b1076fa3a01135b5780637ee9857f90
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298466"
---
# <a name="sqlfreestmt"></a>Функция SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Как правило   
      Не рекомендуется применять функцию**SQLFreeStmt** в ODBC 3.0 и более поздних версиях. Однако, если приложению необходимо повторно использовать заявление, вы все равно должны использовать **S'LFreeStmt** с **SQL_RESET_PARAMS** и **SQL_UNBIND** опций). Кроме того, для замены или дублирования функции **S'LFreeStmt** можно также использовать [S'LCloseCursor,](../../relational-databases/native-client-odbc-api/sqlclosecursor.md) [S'LBindParameter,](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) [S'LBindCol,](../../relational-databases/native-client-odbc-api/sqlbindcol.md) [S'LSetDesccField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)и [S'LFreeHandle.](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)  
  
 В целом, более эффективно повторно использовать операторы, чем отбросить их и выделить новые. Однако в некоторых ситуациях, таких как повторное использование инструкций, все еще необходимо использовать s'LFreeStmt.  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LFreeStmt](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
