---
title: Привязка столбцов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fca4cfb1455c91ca57f7b1769266e2040d6a3511
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301825"
---
# <a name="binding-columns"></a>Привязка столбцов
Данные, полученные из источника данных, возвращаются в приложение в переменных, выделенных приложением для этой цели. Прежде чем это можно будет сделать, приложение должно связать эти переменные или *привязать*их к столбцам результирующего набора. по сути, этот процесс аналогичен привязке переменных приложения к параметрам инструкции. Когда приложение привязывает переменную к столбцу результирующего набора, она описывает, что драйверу присваивается переменное Address, тип данных и т. д. Драйвер сохраняет эти сведения в структуре, которая поддерживается для этой инструкции, и использует эти сведения для возврата значения из столбца при выборе строки.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка столбцов результирующего набора](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Использование SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
