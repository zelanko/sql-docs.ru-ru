---
title: + (Объединение строк) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- +
dev_langs:
- kbMDX
helpviewer_keywords:
- string concatenation operators
- + (string concatenation)
ms.assetid: d77636b1-2973-4587-af35-54aba5700d9a
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6ce74b5fb7e3123db674e318cf8340fed974c591
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="-string-concatenation-mdx"></a>+ (объединение строк) (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Замечания  
 Оба выражения должны иметь одинаковый тип данных, или одно из выражений должно допускать неявное преобразование к типу данных другого выражения. Если результатом вычисления одного выражения является значение NULL, оператор возвращает результат вычисления другого выражения.  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
