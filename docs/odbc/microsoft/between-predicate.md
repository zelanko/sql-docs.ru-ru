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
ms.openlocfilehash: 1a0ac99729966acdcb03c2aab0175c34bba0c08a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138120"
---
# <a name="between-predicate"></a>Предикат BETWEEN
Синтаксис:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Возвращает значение true, только если *expression1* больше или равно *expression2* и *expression1* меньше или равно *expression3*.  
  
 Этот синтаксис семантика разных драйверы для баз данных Desktop и Microsoft Jet Database engine. В Microsoft Jet SQL *expression2* может быть больше, чем *expression3* таким образом, чтобы инструкция возвращала значение TRUE только в том случае, если *expression1* больше или равно *expression3*, и *expression1* меньше или равно *expression2*.
