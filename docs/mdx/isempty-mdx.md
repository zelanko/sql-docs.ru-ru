---
title: IsEmpty (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dbed0eba3fec73d7134b1ce21275c28dbd387fcd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224964"
---
# <a name="isempty-mdx"></a>IsEmpty (многомерные выражения)


  Возвращает значение, сообщающее, является ли вычисленное выражение значением пустой ячейки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Value_Expression*  
 Допустимое многомерное выражение, обычно возвращающее координаты ячейки элемента или кортежа.  
  
## <a name="remarks"></a>Примечания  
 **IsEmpty** возвращает **true** Если вычисленное выражение принимает значение пустой ячейки. В противном случае эта функция возвращает **false**.  
  
> [!NOTE]  
>  Свойство элемента по умолчанию — значение элемента.  
  
 **IsEmpty** функция — это единственный способ надежно проверки пустую ячейку, так как значение пустой ячейки имеет особое значение в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Если вычисления выражения значение возвращает ошибку, то функция возвращает **false**. Значение выражения возвращает ошибку, например, в том случае, если ссылка свойств указывает на недопустимое или несуществующее свойство.  
  
 Дополнительные сведения о пустых ячейках см. в документации по OLE DB.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значение TRUE, если мера Internet Sales Amount для текущего элемента иерархии Fiscal в измерении Date возвращает пустую ячейку:  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Работа с пустыми значениями](../mdx/working-with-empty-values.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
