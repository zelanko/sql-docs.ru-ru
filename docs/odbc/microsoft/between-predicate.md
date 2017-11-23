---
title: "МЕЖДУ предикат | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c93e94ff9b4b3c0b4117e3e4b8c3fafd35fac09a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="between-predicate"></a>МЕЖДУ предиката
Синтаксис:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Возвращает значение true, только если *expression1* больше или равно *expression2* и *expression1* меньше или равно *выражение3*.  
  
 Этот синтаксис семантика отличается для драйверов базы данных и ядра Microsoft Jet. В Microsoft Jet SQL *expression2* может быть больше, чем *выражение3* , чтобы инструкция возвращала значение TRUE только в том случае, если *expression1* больше или равно *выражение3*, и *expression1* меньше или равно *expression2*.
