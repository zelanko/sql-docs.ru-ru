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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bb7f0fb02049b6d2f1897c4f495035aee2858f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085496"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: литералы даты, времени и отметок времени
Для обеспечения максимальной совместимости приложения должны передавать литералы даты в каноническом формате ODBC с помощью синтаксиса escape-выражения:  
  
-   Для литералов даты {d '*value*'}, где значение *e имеет*формат "гггг-мм-дд"  
  
-   Для литералов времени {t '*value*'}, где значение *e указано*в формате "чч: мм: СС"  
  
 Для литералов отметок времени {TS '*значение*'} *, где значение*e имеет формат "гггг-мм-дд чч: мм: СС [. f...]".
