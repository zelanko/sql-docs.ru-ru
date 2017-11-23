---
title: "SQLProcedureColumns (драйвер доступа) | Документы Microsoft"
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
helpviewer_keywords:
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1eb6158d8d70aae635b00bcd78d844f4d1443b75
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (драйвер доступа)
> [!NOTE]  
>  В этом разделе сведения драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Разработчики приложений должны искать столбцы, определяемые драйвером, начиная с конца результирующего набора и далее в обратном порядке.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT или SQL_RESULT_COL|  
|ПОРЯДКОВЫЙ НОМЕР|Это столбец специфические для драйвера, который возвращается в конце результирующего набора. Тип SQL столбца является целым.|
