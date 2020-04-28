---
title: = (Равно) (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 189facb54de244ff220b41ec08c8b02faf5a2c27
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68139317"
---
# <a name="-equal-to-mdx"></a>= (равно) (многомерные выражения)


  Выполняет операцию сравнения, определяющую, равно ли значение одного многомерного выражения значению другого многомерного выражения.  
  
> [!NOTE]  
>  Для сравнения объектов используйте оператор [is &#40;многомерного выражения&#41;](../mdx/is-mdx.md) . Например, используйте оператор IS для проверки, является ли текущий элемент на оси запросов конкретным элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MDX_Expression = MDX_Expression   
```  
  
#### <a name="parameters"></a>Параметры  
 *MDX_Expression*  
 Допустимое многомерное выражение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, определяемое исходя из следующих условий.  
  
-   значение **true** , если значение первого параметра равно значению второго параметра.  
  
-   значение **false** , если значение первого параметра не равно значению второго параметра.  
  
-   **значение true** , если оба параметра имеют значение null или один параметр имеет значение null, а другой параметр равен 0.  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показаны примеры этих условий:  
  
 `With`  
  
 `--Returns true`  
  
 `Member [Measures].bool1 as 1=1`  
  
 `--Returns false`  
  
 `Member [Measures].bool2 as 1=0`  
  
 `--Returns true`  
  
 `Member [Measures].bool3 as null=null`  
  
 `--Returns true`  
  
 `Member [Measures].bool4 as 0=null`  
  
 `--Returns false`  
  
 `Member [Measures].bool5 as 1=null`  
  
 `Select {[Measures].bool1,[Measures].bool2,[Measures].bool3,[Measures].bool4,[Measures].bool5}`  
  
 `On 0`  
  
 `From [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-operator-reference-mdx.md)  
  
  
