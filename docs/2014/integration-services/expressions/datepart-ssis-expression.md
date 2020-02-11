---
title: DATEPART (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 22225f9a1791185ed78dfc75d92c3dbced7be3ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62769341"
---
# <a name="datepart-ssis-expression"></a>DATEPART (выражение служб SSIS)
  Возвращает целое число, обозначающее раздел даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a>Аргументы  
 *datepart*  
 Параметр, который указывает, для какой части даты вернуть новое значение.  
  
 *date*  
 Выражение, возвращающее допустимую дату или строку в формате даты.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 DATEPART возвращает NULL при аргументе NULL.  
  
 Литерал даты должен быть явно приведен к одному из типов данных даты. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
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
|Секунда|ss, s|  
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
  
## <a name="see-also"></a>См. также:  
 [DATEADD (выражение служб SSIS)](dateadd-ssis-expression.md)   
 [DATEDIFF (выражение служб SSIS)](datediff-ssis-expression.md)   
 [DAY (выражение служб SSIS)](day-ssis-expression.md)   
 [MONTH (выражение служб SSIS)](month-ssis-expression.md)   
 [YEAR (выражение служб SSIS)](year-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
