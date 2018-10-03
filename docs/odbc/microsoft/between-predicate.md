---
title: Предикат BETWEEN | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4411345d790e64ae9fb21144a7d82ffe4cd45e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690952"
---
# <a name="between-predicate"></a>Предикат BETWEEN
Синтаксис:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Возвращает значение true, только если *expression1* больше или равно *expression2* и *expression1* меньше или равно *expression3*.  
  
 Этот синтаксис семантика разных драйверы для баз данных Desktop и Microsoft Jet Database engine. В Microsoft Jet SQL *expression2* может быть больше, чем *expression3* таким образом, чтобы инструкция возвращала значение TRUE только в том случае, если *expression1* больше или равно *expression3*, и *expression1* меньше или равно *expression2*.
