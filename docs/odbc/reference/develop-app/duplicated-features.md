---
title: "Дублировать возможности | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b12ba1b5b8c70e6ab0f7efe6f0811984411a6022
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="duplicated-features"></a>Повторяющийся функции
Следующие 2 ODBC. *x* повторяются функции ODBC 3. *x* функции. В результате ODBC 2. *x* функции являются устаревшими в ODBC 3. *x*. ODBC 3. *x* функции называются замены функции.  
  
 Если приложение использует устаревшие ODBC 2. *x* функции и базового драйвера — ODBC 3. *x* драйвера, диспетчер драйверов сопоставляет вызов функции соответствующая функция замены. Единственное исключение из этого правила является **SQLExtendedFetch**. (См. сноска в конце следующей таблице). Дополнительные сведения об этих сопоставлениях см. в разделе [сопоставление устаревшие функции](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
 Если приложение использует функцию замены и базового драйвера является ODBC 2. *x* драйвера, диспетчер драйверов сопоставляет вызов функции соответствующая функция не рекомендуется.  
  
|ODBC 2. *x* функции|ODBC 3. *x* функции|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
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
  
 [1] функция **SQLExtendedFetch** повторяющихся функции; **SQLFetchScroll** предоставляет те же функциональные возможности в ODBC 3. *x*. Тем не менее, диспетчер драйверов не соответствует **SQLExtendedFetch** для **SQLFetchScroll** при переходе от ODBC 3. *x* драйвера. Дополнительные сведения см. в разделе [диспетчера драйверов назначение](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости. Сопоставляет диспетчера драйверов **SQLFetchScroll** для **SQLExtendedFetch** при переходе от ODBC 2. *x* драйвера.  
  
> [!NOTE]  
>  Функция **SQLBindParam** является особым случаем. **SQLBindParam** повторяющихся функциональность. Это не ODBC 2*.x* функции, но функция, которая присутствует в стандартах Open Group и ISO. Функциональные возможности, предоставляемые этой функцией полностью включена в группу по **SQLBindParameter**. В результате диспетчера драйверов сопоставляет вызов **SQLBindParam** для **SQLBindParameter** при базового драйвера ODBC 3. *x* драйвера. Однако когда базового драйвера имеет ODBC 2*.x* драйвера, диспетчер драйверов не выполнять сопоставление.

