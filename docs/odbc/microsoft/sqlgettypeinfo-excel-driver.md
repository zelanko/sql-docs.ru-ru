---
title: SQLGetTypeInfo (драйвер для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Excel Driver
- Excel driver [ODBC], SQLGetTypeInfo
ms.assetid: 708845be-e6a1-4677-8113-c52819a43fa4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 227fef1ecd28e5099b599e86c82c3cc42fbacd0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898711"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo (драйвер для Excel)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемых в таблицу, созданные **SQLGetTypeInfo** будет использоваться имя, чаще всего используется в источнике данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращаться в столбце с возможностью поиска байт, счетчик, Double, Single, долго и Short типов данных. (LIKE возможность достигается путем преобразования значения в символ, с помощью преобразования канонические функции ODBC, выполнению сравнения.)  
  
 Если используется драйвер Microsoft Excel, имена типов ODBC возвращаются в столбце TYPE_NAME, который возвращается **SQLGetTypeInfo**.
