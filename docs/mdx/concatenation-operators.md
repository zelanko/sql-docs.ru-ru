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
ms.openlocfilehash: 7298f80a7d3f61b5b00692be8fbc480429487454
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892462"
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
 Если строки, участвующие в объединении, имеют одинаковые параметры сортировки, результирующая объединенная строка будет иметь те же параметры сортировки, что и исходные строки. В противном случае параметры сортировки результирующей объединенной строки определяются правилами очередности параметров сортировки. Дополнительные сведения см. в разделе [Языки и параметры сортировки (службы Analysis Services)](https://docs.microsoft.com/analysis-services/languages-and-collations-analysis-services).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40;синтаксиса многомерных выражений&#41;](../mdx/operators-mdx-syntax.md)  
  
  
