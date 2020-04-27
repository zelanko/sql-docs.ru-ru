---
title: IsEmpty (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8b31b884e0f86bf2aebe4859cd1c7a441669e813
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905989"
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
  
## <a name="remarks"></a>Remarks  
 Функция **IsEmpty** возвращает **значение true** , если вычисленное выражение является пустым значением ячейки. В противном случае эта функция возвращает **значение false**.  
  
> [!NOTE]  
>  Свойство элемента по умолчанию — значение элемента.  
  
 Функция **IsEmpty** является единственным способом надежного тестирования пустой ячейки, так как значение пустой ячейки в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]может быть специальным.  
  
> [!IMPORTANT]  
>  Если вычисление выражения значения возвращает ошибку, функция возвратит **значение false**. Значение выражения возвращает ошибку, например, в том случае, если ссылка свойств указывает на недопустимое или несуществующее свойство.  
  
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
  
  
