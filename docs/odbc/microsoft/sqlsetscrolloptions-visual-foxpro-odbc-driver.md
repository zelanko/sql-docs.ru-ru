---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c2d78e26309d5ea7dc5e6eed5a04e84a1651b33
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63305740"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Частичный  
  
 Соответствие API ODBC: Уровень 2  
  
 Задает параметры, определяющие поведение курсоров, связанные с дескриптором инструкции, *hstmt*.  
  
 Драйвер ODBC для Visual FoxPro поддерживает только SQL_CONCUR_READ_ONLY; он не поддерживает *fConcurrency* значение SQL_CONCUR_ROWVER. Драйвер преобразует SQL_KEYSET_SIZE SQL_CURSOR_DYNAMIC и SQL_CURSOR_KEYSET_DRIVEN в SQL_SCROLL_STATIC с предупреждением ODBC_01S02.  
  
 Дополнительные сведения см. в разделе [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) в *Справочник по программированию ODBC*.
