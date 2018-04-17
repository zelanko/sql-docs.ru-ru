---
title: Функции ODBC, выполняемая библиотеку курсоров | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: 2f1d3386-7e59-4d55-a5b4-3440b61343a3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 789aae8023a5c4d48b14b6cb91a8d11a41403cac
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-functions-executed-by-the-cursor-library"></a>Функции ODBC, выполняемая библиотеку курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Библиотека курсоров выполняет следующие функции. Когда приложение вызывает функцию в этом списке, диспетчер драйверов вызывает библиотеку курсоров, не драйвер. Обратите внимание, что библиотека курсоров может вызывать драйвер при выполнении функции.  
  
|||  
|-|-|  
|**SQLBindCol**|**SQLGetStmtOption**|  
|**SQLBindParam**|**SQLNativeSql**|  
|**SQLBindParameter**|**SQLNumParams**|  
|**SQLCloseCursor**|**SQLParamOptions**|  
|**SQLEndTran**|**SQLRowCount**|  
|**SQLExtendedFetch**|**SQLSetConnectAttr**|  
|**SQLFetchScroll**|**SQLSetConnectOption**|  
|**SQLFreeHandle**|**SQLSetDescField**|  
|**SQLFreeStmt**|**SQLSetDescRec**|  
|**SQLGetData**|**SQLSetPos**|  
|**SQLGetDescField**|**SQLSetScrollOptions**|  
|**SQLGetDescRec**|**SQLSetStmtAttr**|  
|**SQLGetFunctions**|**SQLSetStmtOption**|  
|**SQLGetInfo**|**SQLTransact**|  
|**SQLGetStmtAttr**||
