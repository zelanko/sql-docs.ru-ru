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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63067850"
---
# <a name="sqlcancel"></a>SQLCancel
  [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) разделе говорится, что в ODBC 2.x, если приложение вызывает `SQLCancel` когда обработка не выполняется в операторе, `SQLCancel` имеет тот же эффект, что `SQLFreeStmt` с `SQL_CLOSE` параметр; это поведение определяется только для полноты информации, и приложение должно вызывать `SQLFreeStmt` или `SQLCloseCursor` закрытия курсора. Но даже если приложение собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет версию ODBC API 3.5.x или более позднюю, функция `SQLCancel` будет использовать поведение ODBC 2.x.  
  
## <a name="see-also"></a>См. также  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
