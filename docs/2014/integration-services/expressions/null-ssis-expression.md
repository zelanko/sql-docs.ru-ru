---
title: NULL (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6659b9390f52bc27c52f82b875d50da3fd37b5ce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102947"
---
# <a name="null-ssis-expression"></a>NULL (выражение служб SSIS)
  Возвращает значение NULL запрошенного типа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Аргументы  
 *typespec*  
 Допустимый тип данных. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Любой допустимый тип данных со значением NULL.  
  
## <a name="remarks"></a>Примечания  
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
 [ISNULL &#40;выражение служб SSIS&#41;](null-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  
