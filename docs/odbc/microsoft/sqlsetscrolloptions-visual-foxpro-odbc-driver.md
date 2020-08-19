---
description: SQLSetScrollOptions (драйвер ODBC для Visual FoxPro)
title: SQLSetScrollOptions (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c0e7cecfb0ce7640575cb69f1e84e805a884b57b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421638"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Соответствие API-интерфейса ODBC: уровень 2  
  
 Задает параметры, управляющие поведением курсоров, связанных с маркером инструкции, *хстмт*.  
  
 Драйвер ODBC для Visual FoxPro поддерживает только SQL_CONCUR_READ_ONLY; Он не поддерживает значение *фконкурренци* SQL_CONCUR_ROWVER. Драйвер преобразует SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC и SQL_CURSOR_KEYSET_DRIVEN в SQL_SCROLL_STATIC с предупреждением ODBC_01S02.  
  
 Дополнительные сведения см. в разделе [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) в *справочнике программиста по ODBC*.
