---
title: МЕЖДУГЕ Предикат (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283862"
---
# <a name="between-predicate"></a>Предикат BETWEEN
Синтаксис выглядит вот так:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 возвращается верно только в том случае, если *expression1* больше или равен *выражению2* и *expression1* меньше или равен *выражению3*.  
  
 Семантика этого синтаксиса отличается для драйверов настольных баз данных и движка Microsoft Jet. В Microsoft Jet *S'L, expression2* может быть больше, чем *expression3,* так что заявление будет возвращаться, только если *expression1* больше или равен *expression3,* а *expression1* меньше или равен *expression2*.
