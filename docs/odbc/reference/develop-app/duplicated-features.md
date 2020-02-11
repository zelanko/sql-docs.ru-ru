---
title: Дублирование компонентов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ca73b5b9b41c99bd6db8e6181fa3582cae47c1d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046902"
---
# <a name="duplicated-features"></a>Повторяющиеся функции
Следующие функции ODBC *2. x* дублируются функциями ODBC *3. x* . В результате функции ODBC *2. x* являются устаревшими в ODBC *3. x*. Функции ODBC *3. x* называются функциями замены.  
  
 Если приложение использует устаревшую функцию ODBC *2. x* , а базовый драйвер — драйвер ODBC *3. x* , диспетчер драйверов сопоставляет вызов функции с соответствующей функцией замены. Единственным исключением из этого правила является **SQLExtendedFetch**. (См. сноску в конце следующей таблицы.) Дополнительные сведения об этих сопоставлениях см. в разделе [сопоставление устаревших функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) в приложении G: рекомендации по драйверу для обеспечения обратной совместимости.  
  
 Если приложение использует функцию замены, а базовый драйвер — драйвер ODBC *2. x* , диспетчер драйверов сопоставляет вызов функции с соответствующей устаревшей функцией.  
  
|Функция ODBC *2. x*|ODBC *3. x,* функция|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**Функцию SQLAllocHandle**|  
|**SQLAllocEnv**|**Функцию SQLAllocHandle**|  
|**SQLAllocStmt**|**Функцию SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**Функции SQLGetDiagRec**|  
|**SQLExtendedFetch**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**, **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] функция **SQLExtendedFetch** дублирует функциональность; **SQLFetchScroll** предоставляет те же функциональные возможности, что и ODBC *3. x*. Однако диспетчер драйверов не сопоставляет **SQLExtendedFetch** с **SQLFetchScroll** при переходе к драйверу ODBC *3. x* . Дополнительные сведения см. в разделе [что делает диспетчер драйверов](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) в приложении G: рекомендации по драйверу для обеспечения обратной совместимости. Диспетчер драйверов сопоставляет **SQLFetchScroll** с **SQLExtendedFetch** при переходе к драйверу ODBC *2. x* .  
  
> [!NOTE]
>  Функция **склбиндпарам** является особым случаем. **Склбиндпарам** — это повторяющаяся функциональность. Это не функция ODBC *2. x* , но функция, которая есть в стандартах Open Group и ISO. Функциональные возможности, предоставляемые этой функцией, полностью относящиеся с помощью **SQLBindParameter**. В результате диспетчер драйверов сопоставляет вызов **склбиндпарам** с **SQLBindParameter** , если базовый драйвер является драйвером ODBC *3. x* . Однако, если базовый драйвер является драйвером ODBC *2. x* , диспетчер драйверов не выполняет это сопоставление.
