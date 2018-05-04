---
title: МЕЖДУ предикат | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55c86eaca6c79a3e5811223f58a78a9452986800
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="between-predicate"></a>МЕЖДУ предиката
Синтаксис:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Возвращает значение true, только если *expression1* больше или равно *expression2* и *expression1* меньше или равно *выражение3*.  
  
 Этот синтаксис семантика отличается для драйверов базы данных и ядра Microsoft Jet. В Microsoft Jet SQL *expression2* может быть больше, чем *выражение3* , чтобы инструкция возвращала значение TRUE только в том случае, если *expression1* больше или равно *выражение3*, и *expression1* меньше или равно *expression2*.
