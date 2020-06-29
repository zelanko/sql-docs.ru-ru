---
title: MONTH (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], MONTH
- MONTH function
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d587a860ad402c8a7458bb148741b753f3aeb2ae
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437231"
---
# <a name="month-ssis-expression"></a>MONTH (выражение служб SSIS)
  Возвращает целое число, представляющее месяц указанной даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MONTH(date)  
```  
  
## <a name="arguments"></a>Аргументы  
 *date*  
 Является датой в любом формате дат.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 Функция MONTH возвращает значение NULL, если значение аргумента NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  Проверка выражения завершается ошибкой при явном приведении литерала даты к одному из следующих типов данных: DT_DBTIMESTAMPOFFSET и DT_DBTIMESTAMP2.  
  
 Использование функции MONTH более компактно, но эквивалентно использованию функции DATEPART(«Month», date).  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере возвращается номер месяца из литерала даты. Если дата имеет формат «мм/дд/гггг», то этот пример возвращает 11.  
  
```  
MONTH((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 В этом примере возвращается целое число, представляющее месяц в столбце **ModifiedDate** .  
  
```  
MONTH(ModifiedDate)  
```  
  
 В этом примере возвращается целое число, представляющее месяц текущей даты.  
  
```  
MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>См. также:  
 [DATEADD (выражение служб SSIS)](dateadd-ssis-expression.md)   
 [DATEDIFF (выражение служб SSIS)](datediff-ssis-expression.md)   
 [DATEPART (выражение служб SSIS)](datepart-ssis-expression.md)   
 [DAY (выражение служб SSIS)](day-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](year-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
