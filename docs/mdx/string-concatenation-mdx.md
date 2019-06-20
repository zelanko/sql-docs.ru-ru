---
title: + (Объединение строк) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 292d671fb3b971c30b6e261e3b851aba1ead9b36
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150004"
---
# <a name="-string-concatenation-mdx"></a>+ (объединение строк) (многомерные выражения)


  Выполняет строковую операцию сцепления двух или более символьных строк, кортежей или сочетаний строк и кортежей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
String_Expression + String_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *String_Expression*  
 Допустимое многомерное выражение, возвращающее строковое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение с типом данных параметра, имеющего более высокий приоритет.  
  
## <a name="remarks"></a>Примечания  
 Оба выражения должны иметь одинаковый тип данных, или одно из выражений должно допускать неявное преобразование к типу данных другого выражения. Если результатом вычисления одного выражения является значение NULL, оператор возвращает результат вычисления другого выражения.  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
