---
title: Операторы объединения | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 235320a65bf04e8b0ce1d7c23da588a4d541a0b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915863"
---
# <a name="concatenation-operators"></a>Операторы объединения


  Оператором объединения является знак плюс (+). Можно объединить две или более символьные строки в одну символьную строку. Кроме того, можно выполнять объединение двоичных строк.  
  
 В следующем примере с помощью оператора объединения выполняется объединение имени продукта и уникального имени продукта.  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>Дополнительные сведения  
 Если строки, участвующие в объединении, имеют одинаковые параметры сортировки, результирующая объединенная строка будет иметь те же параметры сортировки, что и исходные строки. В противном случае параметры сортировки результирующей объединенной строки определяются правилами очередности параметров сортировки. Дополнительные сведения см. в разделе [Языки и параметры сортировки (службы Analysis Services)](../analysis-services/languages-and-collations-analysis-services.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по операторам многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40;синтаксис многомерных Выражений&#41;](../mdx/operators-mdx-syntax.md)  
  
  
