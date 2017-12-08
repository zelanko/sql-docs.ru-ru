---
title: "На уровне элемента (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8430e055cb366420af51d8045381da1aacf78e3e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="level-element-csdlbi"></a>Элемент Level (CSDLBI)
  Элемент Level — это сложный тип, который определяет один уровень в иерархии  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент Level.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Source|Да|Контейнер для ссылки на свойство.|  
|PropertyRef|Да|Ссылка на свойство экземпляра. Другие атрибуты уровня, например заголовки, имя и имя ссылки, могут браться из указанного свойства экземпляра. В этом случае нет необходимости задавать их в элементе Level.|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения об иерархиях в табличных моделях см. в разделе [Элемент Hierarchy (CSDLBI)](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 показывается определение множественных уровней в иерархии в образце табличной модели AdventureWorks.  
  
```  
  
<bi:Hierarchy Name="Category">  
   <bi:Level Name="CategoryName">  
     <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
     </bi:Source>  
   </bi:Level>  
   <bi:Level Name="ProductName">  
     <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
     </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 В следующем примере для CSDLBI версии 1.1 показана иерархия с несколькими уровнями из куба операций Contoso.  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
     <bi:Documentation>  
        <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
     </bi:Documentation>  
  
     <bi:Level Name="ProductLine">  
        <bi:Source>  
        <bi:PropertyRef Name="ProductLine" />  
        </bi:Source>  
     </bi:Level>  
  
     <bi:Level Name="ModelName">  
        <bi:Source>  
        <bi:PropertyRef Name="ModelName" />  
        </bi:Source>  
     </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Общие сведения о функциях для иерархий родители потомки в DAX](http://msdn.microsoft.com/en-us/b11f0cff-cee4-4ae7-a5b3-ebe288fc42d3)   
 [Настроить &#40; Все &#41; Уровне для иерархий атрибутов](../../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
