---
title: Элемент Hierarchy (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 99884f036225b8070e8c78f03836fa1c48b2f9c6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="hierarchy-element-csdlbi"></a>Элемент Hierarchy (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Элемент Hierarchy — логический контейнер для полей таблицы, который можно соединить друг с другом в некоторого вида иерархическую структуру. Элемент Hierarchy является производным элемента языка CSDL Member и расширен так, чтобы поддерживать иерархии, созданные в моделях данных бизнес-аналитики.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент Hierarchy  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Документация|Нет|Описание иерархии.|  
|Level|Да|Один или несколько элементов Level, определяющих столбцы, участвующие в иерархии.<br /><br /> См. раздел [Элемент Level (CSDLBI)](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/level-element-csdlbi.md).|  
  
## <a name="remarks"></a>Замечания  
 В табличных моделях иерархии создаются за счет определения отношений «родитель-потомок» между столбцами одной таблицы. Дополнительные сведения см. в разделе [иерархий](../../../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
## <a name="example"></a>Пример  
 **Табличные**  
  
 В следующем примере для CSDLBI версии 1.0 показана иерархия в примере модели AdventureWorks, добавленная к таблице Products.  
  
```  
  
<bi:Hierarchy Name="Categoryy">  
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
 **Многомерные**  
  
 В следующем примере для CSDLBI версии 1.1 показана иерархия в кубе Contoso Retail Operations.  
  
```  
  
<bi:Hierarchy Name="Product_Hierarchy" Caption="Product Hierarchy" ReferenceName="Product Hierarchy">  
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
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Общие сведения о функциях для иерархий родители потомки в DAX](http://msdn.microsoft.com/en-us/b11f0cff-cee4-4ae7-a5b3-ebe288fc42d3)   
 [Настроить & #40; Все & #41; Уровне для иерархий атрибутов](../../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
