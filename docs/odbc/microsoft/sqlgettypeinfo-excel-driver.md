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
manager: craigg
ms.openlocfilehash: ac7fe52ffdbb090e0b63a972e77c1a7f7a756446
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63034911"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo (драйвер для Excel)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемых в таблицу, созданные **SQLGetTypeInfo** будет использоваться имя, чаще всего используется в источнике данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращаться в столбце с возможностью поиска байт, счетчик, Double, Single, долго и Short типов данных. (LIKE возможность достигается путем преобразования значения в символ, с помощью преобразования канонические функции ODBC, выполнению сравнения.)  
  
 Если используется драйвер Microsoft Excel, имена типов ODBC возвращаются в столбце TYPE_NAME, который возвращается **SQLGetTypeInfo**.
