---
title: LIKE Предикат Побег Характер (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e4f04b12911145eede3354532736cb92f1ae413
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306155"
---
# <a name="like-predicate-escape-character"></a>Escape-символ предиката LIKE
В предикате **LIKE** знак процента (%) соответствует нулю или более любого символа, и подчеркивание (я) соответствует любому одному символу. Чтобы соответствовать фактическому знаку процента или подчеркнуть в предикате **LIKE,** персонаж побега должен прийти до знака процента или подчеркнуть. Последовательность побега, которая определяет **like** предикатный персонаж побега:  
  
 **«побег»** *побег-символ* **')**  
  
 где *побег-символ* любой символ поддерживается источником данных.  
  
 Для получения более подробной информации о последовательности побега LIKE [см.](../../../odbc/reference/appendixes/like-escape-sequence.md)  
  
 Например, следующие операторы S'L создают тот же набор имен клиентов, который начинается с символов "%AAA". В первом заявлении используется синтаксис побега-последовательности. Второе утверждение использует родной синтаксис для Microsoft® Access и не совместимо. Обратите внимание, что второй процент символа в каждом предикате **LIKE** является символом подстановочного знака, который соответствует нулю или более любого символа.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Чтобы определить, поддерживается ли символ побега **предикатом LIKE** источником данных, приложение вызывает **s'LGetInfo** с SQL_LIKE_ESCAPE_CLAUSE опцией.
