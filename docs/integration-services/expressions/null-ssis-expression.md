---
title: "NULL (выражение служб SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 29f3820518e10bf0b4066d7cf3e8e11d9e50ce3c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="null-ssis-expression"></a>NULL (выражение служб SSIS)
  Возвращает значение NULL запрошенного типа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Аргументы  
 *typespec*  
 Допустимый тип данных. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Любой допустимый тип данных со значением NULL.  
  
## <a name="remarks"></a>Замечания  
 Функция NULL возвращает NULL, если аргумент NULL.  
  
 Для некоторых типов данных чтобы запросить значения NULL, необходимы параметры. В следующей таблице приведены эти типы данных и их параметры.  
  
|Тип данных|Параметр|Пример|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|(DT_STR,30,1252) приводит 30 символов к типу данных DT_STR, используя кодовую страницу 1252.|  
|DT_WSTR|*charcount*|(DT_WSTR,20) приводит 20 символов к типу данных DT_WSTR.|  
|DT_BYTES|*bytecount*|(DT_BYTES,50) приводит 50 байт к типу данных DT_BYTES.|  
|DT_DECIMAL|*масштаб*|(DT_DECIMAL,2) приводит числовое значение к типу данных DT_DECIMAL, используя масштаб 2.|  
|DT_NUMERIC|*precision*<br /><br /> *масштаб*|(DT_NUMERIC,10,3) приводит числовое значение к типу данных DT_NUMERIC, используя точность 10 и масштаб 3.|  
|DT_TEXT|*codepage*|(DT_TEXT,1252) приводит значение к типу данных DT_TEXT, используя кодовую страницу 1252.|  
  
## <a name="expression-examples"></a>Примеры выражений  
 Эти примеры возвращают значение NULL следующих типов данных: DT_STR, DT_DATE и DT_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a>См. также  
 [ISNULL (выражение служб SSIS)](../../integration-services/expressions/isnull-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
