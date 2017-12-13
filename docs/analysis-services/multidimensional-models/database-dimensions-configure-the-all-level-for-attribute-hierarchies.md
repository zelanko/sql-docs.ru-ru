---
title: "Настройка уровня «все» для иерархий атрибутов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 95e32a7c6aeec0acd9a383293732a09d32333865
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="database-dimensions---configure-the-all-level-for-attribute-hierarchies"></a>Измерения базы данных — Настройка уровня «все» для иерархий атрибутов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], уровень (все) представляет собой уровень необязательно, сформированные системой. Он содержит только один элемент, значение которого является результатом статистической обработки значений всех членов на ближайшем подчиненном уровне. Этот элемент называется «Все». Он создается системой и отсутствует в таблице измерений. Поскольку элемент уровня «Все» находится на вершине иерархии, его значение является результатом статистической обработки значений всех элементов иерархии. Элемент (Все) часто служит в качестве члена иерархии по умолчанию.  
  
 Присутствие уровня (Все) в иерархии атрибутов определяет свойство **IsAggregatable** атрибута, а наличие уровня (Все) в пользовательской иерархии — свойство **IsAggregatable** атрибута на верхнем ее уровне. Уровень (Все) существует, если свойство **IsAggregatable** имеет значение **True**. Уровня (Все) не будет в иерархии, если свойство **IsAggregatable** имеет значение **False**.  
  
## <a name="establishing-the-topmost-level"></a>Установление высшего уровня  
 Если свойство **IsAggregatable** исходного атрибута уровня иерархии имеет значение **False** , то выше этого уровня не могут появляться уровни, подлежащие статистической обработке. Уровень, не подлежащий статистической обработке, должен быть высшим уровнем иерархии. В противном случае свойство **IsAggregatable** исходных атрибутов всех уровней выше этого должно также иметь значение **False**.  
  
## <a name="all-member-and-all-level"></a>Уровень (Все) и элемент «Все»  
 Единственный элемент уровня (Все) называется элементом «Все». Свойство **AttributeAllMemberName**измерения задает имя элемента "Все" для атрибутов измерения. Свойство **AllMemberName** иерархии задает имя элемента «Все» для иерархии.  
  
## <a name="see-also"></a>См. также  
 [Определение элемента по умолчанию](../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
