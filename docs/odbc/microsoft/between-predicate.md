---
title: МЕЖДУ предикатами | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f3ff800938574bec81e9cbb86839e014085a2a8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283862"
---
# <a name="between-predicate"></a>Предикат BETWEEN
Синтаксис выглядит вот так:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Возвращает значение true, только если *expression1* больше или равно *Expression2* , а *expression1* меньше или равно *expression3*.  
  
 Семантика этого синтаксиса различается для драйверов баз данных для настольных систем и ядра Microsoft Jet. В Microsoft Jet SQL выражение *Expression2* может быть больше *expression3* , чтобы инструкция возвращала значение true только в том случае, если *expression1* больше или равно *expression3*, а *expression1* меньше или равно *Expression2*.
