---
description: SQLGetTypeInfo (драйвер для Paradox)
title: SQLGetTypeInfo (Драйвер Paradox) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bedb9170ba18b04e47f9e56bdc47098b9182f8b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339950"
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (драйвер для Paradox)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу Paradox. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемое в таблице, созданной функцией **SQLGetTypeInfo** , будет именем, наиболее часто используемым источником данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращен в столбце с возможностью поиска для типов данных Byte, Counter, Double, Single, long и Short. (ПОДОБная возможность может быть достигнута путем преобразования значения в символ с помощью канонических функций преобразования ODBC и последующего выполнения сравнения).
