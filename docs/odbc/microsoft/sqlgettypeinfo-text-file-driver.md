---
title: SQLGetTypeInfo (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetTypeInfo
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2659b3251cf77882f3762ce5699c36441e6c8ebc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898651"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверам текстовых файлов. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемое в таблице, созданной функцией **SQLGetTypeInfo** , будет именем, наиболее часто используемым источником данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращен в столбце с возможностью поиска для типов данных Byte, Counter, Double, Single, long и Short. (ПОДОБная возможность может быть достигнута путем преобразования значения в символ с помощью канонических функций преобразования ODBC, после чего выполняется сравнение).  
  
 При использовании текстового драйвера **SQLGetTypeInfo** возвращает CASE_SENSITIVE значение false для текстовых типов данных (char и лонгчар), если типы данных фактически учитывают регистр.
