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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 711652e22318d089b02fe8e79cb592f0a42dfff9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81295134"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (драйвер для dBASE)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу dBASE. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемое в таблице, созданной функцией **SQLGetTypeInfo** , будет именем, наиболее часто используемым источником данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращен в столбце с возможностью поиска для типов данных Byte, Counter, Double, Single, long и Short. (ПОДОБная возможность может быть достигнута путем преобразования значения в символ с помощью канонических функций преобразования ODBC, после чего выполняется сравнение).
