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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: edd946ca865cd9d8d2edff2c7bedbb3b2629c97c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299004"
---
# <a name="consistency-check"></a>Проверка согласованности
Проверка согласованности выполняется драйвером автоматически всякий раз, когда приложение задает SQL_DESC_DATA_PTR поле APD, АРД или IPD. Если это поле задано, драйвер проверяет, являются ли значения поля SQL_DESC_TYPE и значения, применимые к полю SQL_DESC_TYPE в той же записи, допустимыми и согласованными.  
  
 Поле SQL_DESC_DATA_PTR IPD обычно не задано. Однако приложение может сделать это для принудительной проверки согласованности полей IPD. Значение поля SQL_DESC_DATA_PTR IPD, равное, не сохраняется и не может быть извлечено вызовом **SQLGetDescField** или **SQLGetDescRec**; Этот параметр устанавливается только для принудительной проверки согласованности. Невозможно выполнить проверку согласованности для IRD.  
  
 Дополнительные сведения о проверке согласованности см. в разделе [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
