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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a634a553672b83931091056dd489f7559c4269b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106208"
---
# <a name="binding-columns"></a>Привязка столбцов
Данные, полученные из источника данных, возвращаются в приложение в переменных, выделенных приложением для этой цели. Прежде чем это можно будет сделать, приложение должно связать эти переменные или *привязать*их к столбцам результирующего набора. по сути, этот процесс аналогичен привязке переменных приложения к параметрам инструкции. Когда приложение привязывает переменную к столбцу результирующего набора, она описывает, что драйверу присваивается переменное Address, тип данных и т. д. Драйвер сохраняет эти сведения в структуре, которая поддерживается для этой инструкции, и использует эти сведения для возврата значения из столбца при выборе строки.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка столбцов результирующего набора](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Использование SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
