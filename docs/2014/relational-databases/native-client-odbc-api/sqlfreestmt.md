---
title: SQLFreeStmt | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16add1df2294e990a5774392b191949b2a8088ff
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425423"
---
# <a name="sqlfreestmt"></a>Функция SQLFreeStmt
  Не рекомендуется применять функцию**SQLFreeStmt** в ODBC 3.0 и более поздних версиях. Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает все определенные значения *Option* для функции **SQLFreeStmt**. Тем не менее, функции [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**и [SQLFreeHandle](sqlfreehandle.md) заменяют или дублируют функцию **SQLFreeStmt** , и должны использоваться вместо нее.  
  
## <a name="see-also"></a>См. также  
 [SQLFreeStmt, функция](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
