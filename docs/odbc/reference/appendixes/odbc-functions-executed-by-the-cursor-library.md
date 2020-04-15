---
title: Функции ODBC, выполненные Библиотекой Курсора (ru) Документы Майкрософт
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
ms.openlocfilehash: 70fb48a8764a913ea4c2376c1a44bcd8712e7d29
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298234"
---
# <a name="odbc-functions-executed-by-the-cursor-library"></a>Функции ODBC, выполняемые библиотекой курсоров
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсора выполняет следующие функции. Когда приложение вызывает функцию в этом списке, менеджер драйвера вызывает библиотеку курсора, а не драйвер. Обратите внимание, что библиотека курсора может вызывать драйвер при выполнения функции.  
  
|||  
|-|-|  
|**SQLBindCol**|**СЗЛГетСтмтOption**|  
|**СЗЛБиндпарам**|**SQLNativeSql**|  
|**SQLBindParameter**|**SQLNumParams**|  
|**SQLCloseCursor**|**СЗЛПарамОпции**|  
|**SQLEndTran**|**SQLRowCount**|  
|**Sqlextendedfetch**|**SQLSetConnectAttr**|  
|**SQLFetchScroll**|**СЗЛЕтКоннектОпция**|  
|**SQLFreeHandle**|**SQLSetDescField**|  
|**Функция SQLFreeStmt**|**SQLSetDescRec**|  
|**SQLGetData**|**функция SQLSetPos;**|  
|**SQLGetDescField**|**СЗЛСЕтПрокрутисОпции**|  
|**SQLGetDescRec**|**SQLSetStmtAttr**|  
|**SQLGetFunctions**|**СЗЛСетСтмтOption**|  
|**SQLGetInfo**|**СЗЛТрансакт**|  
|**SQLGetStmtAttr**||
