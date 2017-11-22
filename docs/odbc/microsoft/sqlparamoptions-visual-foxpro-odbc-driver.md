---
title: "SQLParamOptions (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
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
helpviewer_keywords: SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 47dc4be8925623a9dad87f1f7233211956ea5b67
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Позволяет приложению указать несколько значений в наборе параметров, присвоенный [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). Возможность указать несколько значений для набора параметров полезен для операции массовой вставки и другие типы работ, который требуется источник данных для обработки той же инструкции SQL несколько раз с различными значениями параметров. Например, приложение может указать значения для набора параметров, связанных с **вставить** инструкции, а затем выполните **вставить** один раз для выполнения трех инструкции insert операции.  
  
 Дополнительные сведения см. в разделе [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) в *справочнике программиста ODBC*.
