---
title: NULL (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d4750f030dc1193ef8ed8be1b14198ca21e99be6
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71288727"
---
# <a name="null-ssis-expression"></a>NULL (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Возвращает значение NULL запрошенного типа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Аргументы  
 *typespec*  
 Допустимый тип данных. Дополнительные сведения см. в разделе [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Любой допустимый тип данных со значением NULL.  
  
## <a name="remarks"></a>Remarks  
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
  
## <a name="see-also"></a>См. также:  
 [ISNULL (выражение служб SSIS)](../../integration-services/expressions/isnull-ssis-expression.md)   
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
