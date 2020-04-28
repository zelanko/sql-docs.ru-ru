---
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
ms.openlocfilehash: 372b7c1dab1ad8ff000fb88729c3b02e05d4a21c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299942"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: литералы даты, времени и отметок времени
Для обеспечения максимальной совместимости приложения должны передавать литералы даты в каноническом формате ODBC с помощью синтаксиса escape-выражения:  
  
-   Для литералов даты {d '*value*'}, где значение *e имеет*формат "гггг-мм-дд"  
  
-   Для литералов времени {t '*value*'}, где значение *e указано*в формате "чч: мм: СС"  
  
 Для литералов отметок времени {TS '*значение*'} *, где значение*e имеет формат "гггг-мм-дд чч: мм: СС [. f...]".
