---
title: На уровне элемента (CSDLBI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8b932ac5fac719be29bda37f134f9beb06d1483f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104784"
---
# <a name="level-element-csdlbi"></a>Элемент Level (CSDLBI)
  Элемент Level — это сложный тип, который определяет один уровень в иерархии  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент Level.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Source|Да|Контейнер для ссылки на свойство.|  
|PropertyRef|Да|Ссылка на свойство экземпляра. Другие атрибуты уровня, например заголовки, имя и имя ссылки, могут браться из указанного свойства экземпляра. В этом случае нет необходимости задавать их в элементе Level.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения об иерархиях в табличных моделях см. в разделе [Элемент Hierarchy (CSDLBI)](hierarchy-element-csdlbi.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели табличного объекта](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Общие сведения о функциях для иерархий родители потомки в DAX](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [Настройка &#40;все&#41; уровне для иерархий атрибутов](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
