---
title: SQLCancel | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2db2c4b66940a81dd65064ee730cd683e2206a58
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302648"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В разделе [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) говорится, что в ODBC 2. x, если приложение вызывает **SQLCancel** , когда в инструкции не выполняется обработка, **SQLCancel** действует так же, как **SQLFreeStmt** с параметром **SQL_CLOSE** . Это поведение определено только для полноты, и приложения должны вызывать **SQLFreeStmt** или **SQLCloseCursor** для закрытия курсоров. Но даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственное клиентское приложение устанавливает версию API ODBC 3.5. x или более поздней версии, функция **SQLCancel** будет использовать поведение ODBC 2. x.  
  
## <a name="see-also"></a>См. также:  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
