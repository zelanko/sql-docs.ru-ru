---
title: КАК escape-символ предиката | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30547551cc1793622eaa981c07bbc002d07a094d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312918"
---
# <a name="like-predicate-escape-character"></a>Escape-символ предиката LIKE
В **как** предикат, знак процента (%) совпадения ноль или более символы и подчеркивания (_) соответствует любому символу. Для поиска фактического процента или символ подчеркивания в **как** предиката, escape-символ должен предшествовать знак процента или символом подчеркивания. Escape-последовательность, которая определяет **как** является escape-символ предиката:  
  
 **{escape "** *escape-символ* **"}**  
  
 где *escape-символ* — это любой символ, поддерживаемых источником данных.  
  
 Дополнительные сведения о LIKE escape-последовательности, см. в разделе [как escape-последовательность](../../../odbc/reference/appendixes/like-escape-sequence.md) в приложение в: Грамматика SQL.  
  
 Например следующие инструкции SQL создать один и тот же результирующий набор клиенту, имена которых начинаются с символов «% AAA». В первой инструкции используется синтаксис escape последовательности. Вторая инструкция имеет собственный синтаксис для Microsoft® Access и не поддерживает взаимодействие. Обратите внимание, что процент второй символ в каждом **как** предикат является подстановочным знаком, который соответствует нулевому или большему любого символа.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Чтобы определить, является ли **как** escape-символ предиката поддерживается источником данных, приложение вызывает **SQLGetInfo** с параметром SQL_LIKE_ESCAPE_CLAUSE.
