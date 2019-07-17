---
title: Настройка уровня «все» для иерархий атрибутов | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 23b00a88c8abf80045a38d0b8cc5d0c695949b0b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178905"
---
# <a name="database-dimensions---configure-the-all-level-for-attribute-hierarchies"></a>Измерения базы данных — настройка уровня "Все" для иерархий атрибутов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]уровень "Все" является дополнительным, сформированным системой. Он содержит только один элемент, значение которого является результатом статистической обработки значений всех членов на ближайшем подчиненном уровне. Этот элемент называется «Все». Он создается системой и отсутствует в таблице измерений. Поскольку элемент уровня «Все» находится на вершине иерархии, его значение является результатом статистической обработки значений всех элементов иерархии. Элемент (Все) часто служит в качестве члена иерархии по умолчанию.  
  
 Присутствие уровня (Все) в иерархии атрибутов определяет свойство **IsAggregatable** атрибута, а наличие уровня (Все) в пользовательской иерархии — свойство **IsAggregatable** атрибута на верхнем ее уровне. Уровень (Все) существует, если свойство **IsAggregatable** имеет значение **True**. Уровня (Все) не будет в иерархии, если свойство **IsAggregatable** имеет значение **False**.  
  
## <a name="establishing-the-topmost-level"></a>Установление высшего уровня  
 Если свойство **IsAggregatable** исходного атрибута уровня иерархии имеет значение **False** , то выше этого уровня не могут появляться уровни, подлежащие статистической обработке. Уровень, не подлежащий статистической обработке, должен быть высшим уровнем иерархии. В противном случае свойство **IsAggregatable** исходных атрибутов всех уровней выше этого должно также иметь значение **False**.  
  
## <a name="all-member-and-all-level"></a>Уровень (Все) и элемент «Все»  
 Единственный элемент уровня (Все) называется элементом «Все». Свойство **AttributeAllMemberName**измерения задает имя элемента "Все" для атрибутов измерения. Свойство **AllMemberName** иерархии задает имя элемента «Все» для иерархии.  
  
## <a name="see-also"></a>См. также  
 [Определение элемента по умолчанию](../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
