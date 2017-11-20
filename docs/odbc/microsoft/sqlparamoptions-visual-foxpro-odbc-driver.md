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
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 17a82974d8531d0524f4bac89701d6c97a05198d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Позволяет приложению указать несколько значений в наборе параметров, присвоенный [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). Возможность указать несколько значений для набора параметров полезен для операции массовой вставки и другие типы работ, который требуется источник данных для обработки той же инструкции SQL несколько раз с различными значениями параметров. Например, приложение может указать значения для набора параметров, связанных с **вставить** инструкции, а затем выполните **вставить** один раз для выполнения трех инструкции insert операции.  
  
 Дополнительные сведения см. в разделе [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) в *справочнике программиста ODBC*.

