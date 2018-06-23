---
title: DATEPART (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5fc80a360a044b72b42ea41af5b5e538c124c6df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109762"
---
# <a name="datepart-ssis-expression"></a>DATEPART (выражение служб SSIS)
  Возвращает целое число, обозначающее раздел даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a>Аргументы  
 *часть_даты*  
 Параметр, который указывает, для какой части даты вернуть новое значение.  
  
 *date*  
 Выражение, возвращающее допустимую дату или строку в формате даты.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Примечания  
 DATEPART возвращает NULL при аргументе NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 В следующей таблице перечислены части дат и сокращения, распознаваемые средством оценки выражений. Имена частей даты обрабатываются без учета регистра.  
  
|часть_даты|Сокращения|  
|--------------|-------------------|  
|Год|yy, yyyy|  
|Квартал|qq, q|  
|Месяц|mm, m|  
|День года|dy, y|  
|День|dd, d|  
|Неделя|wk, ww|  
|День недели|dw|  
|Час|Hh|  
|Минута|mi, n|  
|Вторая|ss, s|  
|Миллисекунда|Ms|  
  
## <a name="ssis-expression-examples"></a>Примеры выражений служб SSIS  
 Этот пример возвращает целое число, которое представляет месяц в литерале даты. Если формат даты «мм/дд/гггг», то этот пример возвращает 11.  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 Этот пример возвращает целое число, представляющее день в столбце **ModifiedDate** .  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 Этот пример возвращает целое число, представляющее год в текущей дате.  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a>См. также  
 [Функция DATEADD &#40;выражение служб SSIS&#41;](dateadd-ssis-expression.md)   
 [Функция DATEDIFF &#40;выражение служб SSIS&#41;](datediff-ssis-expression.md)   
 [DAY (выражение служб SSIS)](day-ssis-expression.md)   
 [MONTH (выражение служб SSIS)](month-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](year-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  