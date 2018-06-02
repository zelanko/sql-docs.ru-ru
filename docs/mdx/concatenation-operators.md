---
title: Операторы объединения | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a59ba79a2ba6cde723b79bb459734e7a8b5d752a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578436"
---
# <a name="concatenation-operators"></a>Операторы объединения
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Справочник по операторам Многомерных &#40;многомерных Выражений&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40;синтаксис многомерных Выражений&#41;](../mdx/operators-mdx-syntax.md)  
  
  
