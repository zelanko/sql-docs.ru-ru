---
description: Escape-символ предиката LIKE
title: Escape-символ предиката LIKE | Документация Майкрософт
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
ms.openlocfilehash: 5304068e21dd6faf0e737a94add0cce177c4dabc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476556"
---
# <a name="like-predicate-escape-character"></a>Escape-символ предиката LIKE
В предикате **Like** знак процента (%) соответствует нулю или нескольким символам, а символ подчеркивания (_) соответствует любому символу. Чтобы сопоставить фактический знак процента или символ подчеркивания в предикате **Like** , перед знаком процента или символом подчеркивания должна быть escape-последовательность. Escape-символ предиката LIKE, который определяет **подобную** последовательность:  
  
 **{** Escape *-символ* **"}**  
  
 где *escape-символ* — любой символ, поддерживаемый источником данных.  
  
 Дополнительные сведения о escape-последовательности LIKE см. в разделе [Like escape-последовательность](../../../odbc/reference/appendixes/like-escape-sequence.md) в приложении C: грамматика SQL.  
  
 Например, следующие инструкции SQL создают тот же результирующий набор имен клиентов, которые начинаются с символов «% AAA». В первой инструкции используется синтаксис escape-последовательности. Вторая инструкция использует собственный синтаксис для Microsoft® Access и не поддерживает взаимодействие. Обратите внимание, что второй символ процента в каждом предикате **Like** является символом-шаблоном, который соответствует нулю или большему числу символов.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Чтобы определить, поддерживается ли в источнике данных escape-символ предиката **Like** , приложение вызывает **SQLGetInfo** с параметром SQL_LIKE_ESCAPE_CLAUSE.
