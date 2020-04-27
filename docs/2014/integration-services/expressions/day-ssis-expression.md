---
title: DAY (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 47140db35618143522ad217f5eda2aa3d4b7507b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62898417"
---
# <a name="day-ssis-expression"></a>DAY (выражение служб SSIS)
  Возвращает целое число, представляющее день указанной даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a>Аргументы  
 *date*  
 Выражение, возвращающее допустимую дату или строку в формате даты.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 Функция DAY возвращает значение NULL, если значение аргумента NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  Проверка выражения завершается ошибкой при явном приведении литерала даты к одному из следующих типов данных: DT_DBTIMESTAMPOFFSET и DT_DBTIMESTAMP2.  
  
 Использование функции DAY более компактно, но эквивалентно использованию функции DATEPART("Day", date).  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере возвращается номер дня из литерала даты. Если дата имеет формат «мм/дд/гггг», будет возвращено значение 23.  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 Этот пример возвращает целое число, представляющее день в столбце **ModifiedDate** .  
  
```  
DAY(ModifiedDate)  
```  
  
 В этом примере возвращается целое число, представляющее день текущей даты.  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a>См. также:  
 [DATEADD (выражение служб SSIS)](dateadd-ssis-expression.md)   
 [DATEDIFF (выражение служб SSIS)](datediff-ssis-expression.md)   
 [DATEPART (выражение служб SSIS)](datepart-ssis-expression.md)   
 [MONTH (выражение служб SSIS)](month-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](year-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
