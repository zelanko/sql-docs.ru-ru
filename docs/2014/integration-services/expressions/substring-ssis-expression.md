---
title: SUBSTRING (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SUBSTRING function
- part of expression returned [Integration Services]
ms.assetid: 3a46748a-f5f8-4a6c-9108-673666754068
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2b749a88a0783e6981cf9fd643412f0ca614e6a2
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58381980"
---
# <a name="substring-ssis-expression"></a>SUBSTRING (выражение служб SSIS)
  Возвращает часть символьного выражения, начинающегося с указанной позиции и имеющего указанную длину. Параметр *position* и параметр *length* должны иметь значение, выраженное целым числом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SUBSTRING(character_expression, position, length)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, из которого извлекаются символы.  
  
 *position*  
 Является целым числом, указывающим, где начинается подстрока.  
  
 *length*  
 Является целым числом, указывающим длину подстроки в виде числа символов.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Примечания  
 SUBSTRING использует однобазовый индекс. Если параметр *position* имеет значение 1, то подстрока начинается с первого символа в значении параметра *character_expression*.  
  
 Функция SUBSTRING работает только типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции SUBSTRING. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
 Функция SUBSTRING возвращает нулевой результат при нулевом аргументе.  
  
 Переменные и столбцы могут использовать все аргументы выражения.  
  
 Аргумент *length* может превышать длину строки. В этом случае функция возвращает остаток строки.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример возвращает из строкового литерала два символа, начинающихся с 4. Возвращаемый результат — «ph».  
  
```  
SUBSTRING("elephant",4,2)  
```  
  
 Этот пример возвращает остаток строкового литерала, начиная с четвертого символа. Возвращаемый результат — «phant». Превышение аргументом *length* размера строки не является ошибкой.  
  
```  
SUBSTRING ("elephant",4,50)  
```  
  
 Этот пример возвращает первую букву из столбца **MiddleName** .  
  
```  
SUBSTRING(MiddleName,1,1)  
```  
  
 Этот пример использует переменные в аргументах *position* и *length* . Если **Start** равно 1, и **Length** равно 5, то функция возвращает первые пять символов столбца **Name** .  
  
```  
SUBSTRING(Name,@Start,@Length)  
```  
  
 Этот пример возвращает четыре последних символа переменной **PostalCode** , начиная с шестого символа.  
  
```  
SUBSTRING (@PostalCode,6,4)  
```  
  
 Этот пример возвращает строку с нулевой длиной из строкового литерала.  
  
```  
SUBSTRING ("Redmond",4,0)  
```  
  
## <a name="see-also"></a>См. также  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
