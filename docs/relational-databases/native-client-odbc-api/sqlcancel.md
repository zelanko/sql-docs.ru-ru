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
ms.openlocfilehash: b55d569b124190d7c6248ed632839ae949af8d33
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004394"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  В разделе [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) говорится, что в ODBC 2. x, если приложение вызывает **SQLCancel** , когда в инструкции не выполняется обработка, **SQLCancel** действует так же, как **SQLFreeStmt** с параметром **SQL_CLOSE** . Это поведение определено только для полноты, и приложения должны вызывать **SQLFreeStmt** или **SQLCloseCursor** для закрытия курсоров. Но даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственное клиентское приложение устанавливает версию API ODBC 3.5. x или более поздней версии, функция **SQLCancel** будет использовать поведение ODBC 2. x.  
  
## <a name="see-also"></a>См. также  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
