---
title: "SQLSetScrollOptions (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 63efd04bc43855c08a6de02d5396bea45eabbc68
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Совместимости API ODBC: Уровень 2  
  
 Задает параметры, которые управляют поведением курсоров, связанные с дескриптором инструкции *hstmt*.  
  
 Драйвер ODBC для Visual FoxPro поддерживает только SQL_CONCUR_READ_ONLY; он не поддерживает *fConcurrency* значение SQL_CONCUR_ROWVER. Драйвер преобразует SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC и SQL_CURSOR_KEYSET_DRIVEN SQL_SCROLL_STATIC с предупреждением ODBC_01S02.  
  
 Дополнительные сведения см. в разделе [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) в *справочнике программиста ODBC*.

