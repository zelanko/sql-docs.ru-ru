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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63190308"
---
# <a name="sqlfreestmt"></a>Функция SQLFreeStmt
  Не рекомендуется применять функцию**SQLFreeStmt** в ODBC 3.0 и более поздних версиях. Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает все определенные значения *Option* для функции **SQLFreeStmt**. Тем не менее, функции [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**и [SQLFreeHandle](sqlfreehandle.md) заменяют или дублируют функцию **SQLFreeStmt** , и должны использоваться вместо нее.  
  
## <a name="see-also"></a>См. также  
 [Функция SQLFreeStmt](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
