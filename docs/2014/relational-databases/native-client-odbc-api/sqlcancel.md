---
title: SQLCancel | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6aff7aea0040e2fd7f86a3ad668b4e4438148497
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193363"
---
# <a name="sqlcancel"></a>SQLCancel
  [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) раздел о том, что в ODBC 2.x, если приложение вызывает `SQLCancel` Если обработка не выполняется в операторе `SQLCancel` действует так же, как `SQLFreeStmt` с `SQL_CLOSE` параметр; это поведение определяется только для полноты и приложения должны вызывать метод `SQLFreeStmt` или `SQLCloseCursor` закрытия курсора. Но даже если приложение собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет версию ODBC API 3.5.x или более позднюю, функция `SQLCancel` будет использовать поведение ODBC 2.x.  
  
## <a name="see-also"></a>См. также  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  