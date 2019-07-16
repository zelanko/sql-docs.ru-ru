---
title: SQLGetTypeInfo (драйвер для Paradox) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c212584972f4a7e329d124cc8512be3b1f7a6b9d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898614"
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (драйвер для Paradox)
> [!NOTE]  
>  Здесь приведены сведения об особенностях драйвер для Paradox. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемых в таблицу, созданные **SQLGetTypeInfo** будет использоваться имя, чаще всего используется в источнике данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращаться в столбце с возможностью поиска байт, счетчик, Double, Single, долго и Short типов данных. (LIKE возможность достигается путем преобразования значения в символ, с помощью преобразования канонические функции ODBC и затем выполняет сравнение.)
