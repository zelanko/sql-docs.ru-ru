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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bad2cc35a30f5c6f5855292ff73635cef6072b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067850"
---
# <a name="sqlcancel"></a>SQLCancel
  В [разделе SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) говорится о том, что в ODBC 2. x, если `SQLCancel` приложение вызывает, когда в инструкции не выполняется никакой обработки `SQLCancel` , действует `SQLFreeStmt` аналогично `SQL_CLOSE` параметру. Это поведение определено только для полноты, и приложения должны `SQLFreeStmt` вызывать `SQLCloseCursor` или закрывать курсоры. Но даже если приложение собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет версию ODBC API 3.5.x или более позднюю, функция `SQLCancel` будет использовать поведение ODBC 2.x.  
  
## <a name="see-also"></a>См. также:  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
