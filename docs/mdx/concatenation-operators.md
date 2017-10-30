---
title: "Операторы объединения | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- concatenation operators [MDX]
ms.assetid: 9e4c181a-b71e-41ec-98a1-ec8b5b5103b1
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ae299577ece2c712504631fb85eeac4499c4d4c7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="concatenation-operators"></a>Операторы объединения
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Операторы &#40; Синтаксис многомерных Выражений &#41;](../mdx/operators-mdx-syntax.md)  
  
  

