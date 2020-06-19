---
title: LEFT (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 13b2a300f36696f24ac36f5ca922e6d5d642c031
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969324"
---
# <a name="left-ssis-expression"></a>LEFT (выражение служб SSIS)
  Возвращает указанное количество символов из крайней левой части заданного символьного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьное выражение, из которого извлекаются символы.  
  
 *number*  
 Является целочисленным выражением, которое указывает количество возвращаемых символов.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 Если *number* длиннее, чем *character_expression*, функция возвращает *character_expression*.  
  
 Если *number* равен нулю, функция возвращает строку нулевой длины.  
  
 Если *number* является отрицательным числом, то функция возвратит ошибку.  
  
 Аргумент *number* может принимать переменные и столбцы.  
  
 Функция LEFT работает только с типом данных DT_WSTR. Аргумент *character_expression* , являющийся строковым литералом или столбцом данных с типом данных DT_STR, неявно приведен к типу данных DT_WSTR до выполнения функции LEFT. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
 LEFT возвращает результат NULL, если аргумент имеет значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В следующем примере используется строковый литерал. Возвращаемым результатом является `"Mountain"`.  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a>См. также:  
 [RIGHT (выражение служб SSIS)](right-ssis-expression.md)   
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
