---
title: Функции ODBC, не выполняемые библиотекой курсоров | Документация Майкрософт
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
ms.assetid: f2941522-75eb-4db9-9468-4800b884dac2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 62fcf860aba5c9f0be80e575428a362a7f3ca588
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100655"
---
# <a name="odbc-functions-not-executed-by-the-cursor-library"></a>Функции ODBC, не выполняемые библиотекой курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Библиотека курсоров не выполняет следующие функции. Когда приложение вызывает одну из этих функций, диспетчер драйверов вызывает драйвер, не библиотеку курсоров.  
  
|||  
|-|-|  
|**SQLFetch**|**SQLGetEnvAttr**|  
|**SQLGetConnectAttr**|**SQLSetDescRec**|  
|**SQLGetDiagField**|**SQLSetEnvAttr**|  
|**SQLGetDiagRec**||
