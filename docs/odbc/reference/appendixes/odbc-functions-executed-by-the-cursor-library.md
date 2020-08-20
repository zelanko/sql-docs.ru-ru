---
description: Функции ODBC, выполняемые библиотекой курсоров
title: Функции ODBC, выполняемые библиотекой курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: 2f1d3386-7e59-4d55-a5b4-3440b61343a3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c49082492a35cb79a35c3a346b85af69dddf159c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466118"
---
# <a name="odbc-functions-executed-by-the-cursor-library"></a>Функции ODBC, выполняемые библиотекой курсоров
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсоров выполняет следующие функции. Когда приложение вызывает функцию из этого списка, диспетчер драйверов вызывает библиотеку курсоров, а не драйвер. Обратите внимание, что библиотека курсоров может вызывать драйвер при выполнении функции.  
  
|||  
|-|-|  
|**SQLBindCol**|**SQLGetStmtOption**|  
|**склбиндпарам**|**SQLNativeSql**|  
|**SQLBindParameter**|**SQLNumParams**|  
|**SQLCloseCursor**|**SQLParamOptions**|  
|**SQLEndTran**|**SQLRowCount**|  
|**SQLExtendedFetch**|**SQLSetConnectAttr**|  
|**SQLFetchScroll**|**SQLSetConnectOption**|  
|**SQLFreeHandle**|**SQLSetDescField**|  
|**Функция SQLFreeStmt**|**SQLSetDescRec**|  
|**SQLGetData**|**функция SQLSetPos;**|  
|**SQLGetDescField**|**SQLSetScrollOptions**|  
|**SQLGetDescRec**|**SQLSetStmtAttr**|  
|**SQLGetFunctions**|**SQLSetStmtOption**|  
|**SQLGetInfo**|**SQLTransact**|  
|**SQLGetStmtAttr**||
