---
title: MONTH (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], MONTH
- MONTH function
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ac7362079175711c7027919abccf246670497545
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173085"
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
  
## <a name="remarks"></a>Примечания  
 Функция MONTH возвращает значение NULL, если значение аргумента NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [DATEADD &#40;выражение служб SSIS&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;выражение служб SSIS&#41;](datediff-ssis-expression.md)   
 [DATEPART (выражение служб SSIS)](datepart-ssis-expression.md)   
 [DAY (выражение служб SSIS)](day-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](year-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  
