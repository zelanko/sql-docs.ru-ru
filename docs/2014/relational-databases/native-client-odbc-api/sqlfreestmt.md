---
title: SQLFreeStmt | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4aa7e597bcfa80d7d45064c844986018d64617d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63190308"
---
# <a name="sqlfreestmt"></a>Функция SQLFreeStmt
  Не рекомендуется применять функцию**SQLFreeStmt** в ODBC 3.0 и более поздних версиях. Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает все определенные значения *Option* для функции **SQLFreeStmt**. Тем не менее, функции [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**и [SQLFreeHandle](sqlfreehandle.md) заменяют или дублируют функцию **SQLFreeStmt** , и должны использоваться вместо нее.  
  
## <a name="see-also"></a>См. также  
 [SQLFreeStmt, функция](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
