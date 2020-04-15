---
title: Функции ODBC не выполняются Библиотекой Курсора (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ff9d685cf4a509b84142d91f76d41eb7ca3508ee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81308045"
---
# <a name="odbc-functions-not-executed-by-the-cursor-library"></a>Функции ODBC, не выполняемые библиотекой курсоров
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсора не выполняет следующие функции. Когда приложение вызывает одну из этих функций, менеджер драйвера вызывает драйвер, а не библиотеку курсора.  
  
|||  
|-|-|  
|**SQLFetch**|**СЗЛГетЕнвТтр**|  
|**SQLGetConnectAttr**|**SQLSetDescRec**|  
|**SQLGetDiagField**|**SQLSetEnvAttr**|  
|**Функции SQLGetDiagRec**||
