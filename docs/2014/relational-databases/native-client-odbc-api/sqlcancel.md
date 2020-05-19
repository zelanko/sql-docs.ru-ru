---
title: SQLCancel | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 54ec9ddb143e97aa61a47ebbf0d2094281e59964
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706365"
---
# <a name="sqlcancel"></a>SQLCancel
  В разделе [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) говорится о том, что в ODBC 2. x, если приложение вызывает, `SQLCancel` когда в инструкции не выполняется обработка, `SQLCancel` имеет тот же результат, что `SQLFreeStmt` `SQL_CLOSE` и параметр. это поведение определено только для полноты, и приложения должны вызывать `SQLFreeStmt` или `SQLCloseCursor` закрывать курсоры. Но даже если приложение собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет версию ODBC API 3.5.x или более позднюю, функция `SQLCancel` будет использовать поведение ODBC 2.x.  
  
## <a name="see-also"></a>См. также  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
