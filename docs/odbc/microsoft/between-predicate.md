---
description: Предикат BETWEEN
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
ms.openlocfilehash: 2f2283f5824e4be0c9702bfe8feef9fe3109849a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500387"
---
# <a name="between-predicate"></a>Предикат BETWEEN
Синтаксис выглядит вот так:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Возвращает значение true, только если *expression1* больше или равно *Expression2* , а *expression1* меньше или равно *expression3*.  
  
 Семантика этого синтаксиса различается для драйверов баз данных для настольных систем и ядра Microsoft Jet. В Microsoft Jet SQL выражение *Expression2* может быть больше *expression3* , чтобы инструкция возвращала значение true только в том случае, если *expression1* больше или равно *expression3*, а *expression1* меньше или равно *Expression2*.
