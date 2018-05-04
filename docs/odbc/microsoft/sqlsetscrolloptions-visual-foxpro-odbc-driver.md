---
title: SQLSetScrollOptions (драйвер ODBC для Visual FoxPro) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22b92ffb804ee7f325367c46a7d78b17c8604d94
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Совместимости API ODBC: Уровень 2  
  
 Задает параметры, которые управляют поведением курсоров, связанные с дескриптором инструкции *hstmt*.  
  
 Драйвер ODBC для Visual FoxPro поддерживает только SQL_CONCUR_READ_ONLY; он не поддерживает *fConcurrency* значение SQL_CONCUR_ROWVER. Драйвер преобразует SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC и SQL_CURSOR_KEYSET_DRIVEN SQL_SCROLL_STATIC с предупреждением ODBC_01S02.  
  
 Дополнительные сведения см. в разделе [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) в *справочнике программиста ODBC*.
