---
description: Проверка согласованности
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ad1ffe0cb7819447a3819d73cd6605347b756ede
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465906"
---
# <a name="consistency-check"></a>Проверка согласованности
Проверка согласованности выполняется драйвером автоматически всякий раз, когда приложение задает SQL_DESC_DATA_PTR поле APD, АРД или IPD. Если это поле задано, драйвер проверяет, являются ли значения поля SQL_DESC_TYPE и значения, применимые к полю SQL_DESC_TYPE в той же записи, допустимыми и согласованными.  
  
 Поле SQL_DESC_DATA_PTR IPD обычно не задано. Однако приложение может сделать это для принудительной проверки согласованности полей IPD. Значение поля SQL_DESC_DATA_PTR IPD, равное, не сохраняется и не может быть извлечено вызовом **SQLGetDescField** или **SQLGetDescRec**; Этот параметр устанавливается только для принудительной проверки согласованности. Невозможно выполнить проверку согласованности для IRD.  
  
 Дополнительные сведения о проверке согласованности см. в разделе [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
