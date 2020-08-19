---
description: 'Jet: литералы даты, времени и отметок времени'
title: 'Jet: литералы даты, времени и отметок времени | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02b2a7c5c633ee891dbcd962786cb1904bfd5df8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449446"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: литералы даты, времени и отметок времени
Для обеспечения максимальной совместимости приложения должны передавать литералы даты в каноническом формате ODBC с помощью синтаксиса escape-выражения:  
  
-   Для литералов даты {d '*value*'}, где значение *e имеет*формат "гггг-мм-дд"  
  
-   Для литералов времени {t '*value*'}, где значение *e указано*в формате "чч: мм: СС"  
  
 Для литералов отметок времени {TS '*значение*'} *, где значение*e имеет формат "гггг-мм-дд чч: мм: СС [. f...]".
