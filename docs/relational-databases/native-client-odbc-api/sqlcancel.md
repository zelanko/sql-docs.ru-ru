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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 80b0ac3e21933c378d67b41f1bbc846f04811ed5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73787657"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В разделе [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) говорится, что в ODBC 2. x, если приложение вызывает **SQLCancel** , когда в инструкции не выполняется обработка, **SQLCancel** действует так же, как **SQLFreeStmt** с параметром **SQL_CLOSE** . Это поведение определено только для полноты, и приложения должны вызывать **SQLFreeStmt** или **SQLCloseCursor** для закрытия курсоров. Но даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственное клиентское приложение устанавливает версию API ODBC 3.5. x или более поздней версии, функция **SQLCancel** будет использовать поведение ODBC 2. x.  
  
## <a name="see-also"></a>См. также:  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
