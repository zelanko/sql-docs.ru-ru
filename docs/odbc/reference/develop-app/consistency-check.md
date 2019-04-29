---
title: Проверка согласованности | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb73d8a4de482f24eae5794232019af9890e3624
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043739"
---
# <a name="consistency-check"></a>Проверка согласованности
Проверка согласованности выполняется с помощью драйвера автоматически каждый раз, когда приложение задает поле SQL_DESC_DATA_PTR в APD, Отменить или IPD. Каждый раз, когда это поле имеет значение, драйвер значение SQL_DESC_TYPE поля и значения, применяемые к поле SQL_DESC_TYPE в той же записи происходит проверка правильны и согласуются.  
  
 Поле SQL_DESC_DATA_PTR IPD обычно не задано; Тем не менее приложение может сделать это для принудительно выполнить проверку согласованности IPD полей. Значение, которое присвоено поле SQL_DESC_DATA_PTR IPD фактически не сохраняются и не удается получить с помощью вызова **SQLGetDescField** или **SQLGetDescRec**; этот параметр устанавливается только для принудительного Проверка согласованности. Невозможно выполнить проверку согласованности в IRD.  
  
 Дополнительные сведения о проверке согласованности см. в разделе [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
