---
description: Привязка столбцов
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
ms.openlocfilehash: 8f3f02ec6487b34a6ca2c973c3115c3940ca8fa9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429436"
---
# <a name="binding-columns"></a>Привязка столбцов
Данные, полученные из источника данных, возвращаются в приложение в переменных, выделенных приложением для этой цели. Прежде чем это можно будет сделать, приложение должно связать эти переменные или *привязать*их к столбцам результирующего набора. по сути, этот процесс аналогичен привязке переменных приложения к параметрам инструкции. Когда приложение привязывает переменную к столбцу результирующего набора, она описывает, что драйверу присваивается переменное Address, тип данных и т. д. Драйвер сохраняет эти сведения в структуре, которая поддерживается для этой инструкции, и использует эти сведения для возврата значения из столбца при выборе строки.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка столбцов результирующего набора](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Использование SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
