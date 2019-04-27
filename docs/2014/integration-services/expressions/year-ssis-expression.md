---
title: YEAR (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4e677a4a0c36f52ae62dfc06cd597ad5401fc8e3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768700"
---
# <a name="year-ssis-expression"></a>YEAR (выражение служб SSIS)
  Возвращает целое число, представляющее год указанной даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a>Аргументы  
 *date*  
 Является датой в любом формате дат.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Примечания  
 Функция YEAR возвращает значение NULL, если аргумент — NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  Выражение проверка завершается ошибкой при явном приведении литерала даты к одному из следующих типов данных: DT_DBTIMESTAMPOFFSET и DT_DBTIMESTAMP2.  
  
 Функция YEAR является более компактным, но эквивалентным вариантом функции DATEPART("Year", date).  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает год из литерала даты. Если дата представлена в формате «мм/дд/гггг», то результатом данного примера будет «2002».  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 Этот пример возвращает целое число, которое представляет собой год столбца **ModifiedDate** .  
  
```  
YEAR(ModifiedDate)  
```  
  
 Этот пример возвращает целое число, представляющее год в текущей дате.  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a>См. также  
 [DATEADD (выражение служб SSIS)](dateadd-ssis-expression.md)   
 [DATEDIFF (выражение служб SSIS)](datediff-ssis-expression.md)   
 [DATEPART (выражение служб SSIS)](datepart-ssis-expression.md)   
 [DAY (выражение служб SSIS)](day-ssis-expression.md)   
 [MONTH (выражение служб SSIS)](month-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
