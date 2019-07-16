---
title: 'Jet: Литералы отметки времени, даты и времени | Документация Майкрософт'
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085496"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Литералы даты, времени и отметок времени
Для максимальной совместимости приложений следует передавать литералы даты в канонический формат ODBC с использованием синтаксиса escape-предложении:  
  
-   Для литералов даты {d '*значение*"}, где *значени*e указывается в формате «гггг мм дд»  
  
-   Для литералов времени {t '*значение*"}, где *значени*e указывается в формате «чч: мм:»  
  
 Для отметки времени литералов {ts'*значение*"}, где *значени*e указывается в формате «гггг мм дд чч: мм: [. f...]».
