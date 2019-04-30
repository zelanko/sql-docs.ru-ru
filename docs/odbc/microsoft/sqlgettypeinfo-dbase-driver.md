---
title: SQLGetTypeInfo (драйвер для dBASE) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetTypeInfo
ms.assetid: 6e9ce02b-97c7-4c1a-91e0-829df7459c84
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90bfbe29fd011f8b62527854f0ca5a179d8f63cc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224530"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (драйвер для dBASE)
> [!NOTE]  
>  В этом разделе сведения для dBASE специфические для драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемых в таблицу, созданные **SQLGetTypeInfo** будет использоваться имя, чаще всего используется в источнике данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращаться в столбце с возможностью поиска байт, счетчик, Double, Single, долго и Short типов данных. (LIKE возможность достигается путем преобразования значения в символ, с помощью преобразования канонические функции ODBC, выполнению сравнения.)
