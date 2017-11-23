---
title: "SQLPrepare (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 53b3631e1f5a1827e9ebd18e0ed1537d5772a5ee
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Уровень Core  
  
 Подготавливает инструкцию SQL, планируя как оптимизировать и выполнить инструкцию. Инструкция SQL компилируется для исполнения [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 Если на таблицу, представление или имена полей содержат пробелы, заключите имена кавычка после метки ('). Например если база данных содержит таблицу с именем My таблицу и поле Мое поле, заключите каждый элемент идентификатора следующим образом:  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 Дополнительные сведения см. в разделе [SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md) в *справочнике программиста ODBC*.
