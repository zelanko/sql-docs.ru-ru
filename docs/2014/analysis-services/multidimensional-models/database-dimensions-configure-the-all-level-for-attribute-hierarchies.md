---
title: Настройка уровня «все» для иерархий атрибутов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95e1693333bbc228e16d01646283d41138d0aaf0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075998"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a>Настройка уровня «Все» для иерархий атрибутов
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] В [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]уровень (все) является необязательным, созданным системой уровнем. Он содержит только один элемент, значение которого является результатом статистической обработки значений всех членов на ближайшем подчиненном уровне. Этот элемент называется «Все». Он создается системой и отсутствует в таблице измерений. Поскольку элемент уровня «Все» находится на вершине иерархии, его значение является результатом статистической обработки значений всех элементов иерархии. Элемент (Все) часто служит в качестве члена иерархии по умолчанию.  
  
 Присутствие уровня «Все» в иерархии атрибутов определяет свойство `IsAggregatable` атрибута, а наличие уровня «Все» в пользовательской иерархии — свойство `IsAggregatable` атрибута на верхнем ее уровне. Уровень (Все) существует, если свойство `IsAggregatable` имеет значение `True`. Уровня (Все) не будет в иерархии, если свойство `IsAggregatable` имеет значение `False`.  
  
## <a name="establishing-the-topmost-level"></a>Установление высшего уровня  
 Если свойство `IsAggregatable` исходного атрибута уровня иерархии имеет значение `False`, то выше этого уровня не могут появляться уровни, подлежащие статистической обработке. Уровень, не подлежащий статистической обработке, должен быть высшим уровнем иерархии. В противном случае свойство `IsAggregatable` исходных атрибутов всех уровней выше этого должно также иметь значение `False`.  
  
## <a name="all-member-and-all-level"></a>Уровень (Все) и элемент «Все»  
 Единственный элемент уровня (Все) называется элементом «Все». `AttributeAllMemberName`Свойство в измерении задает имя элемента «все» для атрибутов в измерении. Свойство `AllMemberName` иерархии задает имя элемента «Все» для иерархии.  
  
## <a name="see-also"></a>См. также:  
 [Определение элемента по умолчанию](attribute-properties-define-a-default-member.md)  
  
  
