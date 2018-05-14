---
title: Элемент DisplayKey (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01c6272e3007202bae4f3f2f595579fc095ddc5a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="displaykey-element-csdlbi"></a>Элемент DisplayKey (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Элемент DisplayKey содержит следующий список элементов, составляющих вместе строгий идентификатор. DisplayKey встречается только как дочерний элемент EntityType. Он может ссылаться на столбцы или окончания роли.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены атрибуты элемента DisplayKey.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|IsDisplayKey|Нет|True или False.|  
  
## <a name="remarks"></a>Замечания  
 Этот элемент предназначен для отчетов. Элемент, к которому применяется этот атрибут, не обязательно должен быть фактическим ключом таблицы, а только лишь элементом, представляемым в виде ключа. Однако столбец, используемый для DisplayKey, должен содержать уникальные значения.  
  
## <a name="example"></a>Пример  
 **Табличные**  
  
 В следующем примере для CSDLBI версии 1.1 приведен столбец из примера модели AdventureWorks, который назначен как DisplayKey для таблицы.  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>Пример  
 **Многомерные**  
  
 В следующем примере для CSDLBI версии 1.1 приведена выборка из представления куба операций Contoso. В этой модели столбец Color был помечен в качестве отображаемого ключа для таблицы Bikes.  
  
```  
  
<EntityType   
    Name="Bike">  
.. .. ..  
<Property   
    Name="Color"   
    Type="String"   
    MaxLength="Max"   
    Unicode="true"   
    FixedLength="false">  
<bi:Property   
    ContextualNameRule="Context"   
    Alignment="Left" Units="counts"   
    SortDirection="Descending"   
    IsRightToLeft="true"   
    DefaultAggregateFunction="Max" />  
</Property>  
.. .. ..  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>>  
.. .. ..  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Основные понятия CSDLBI](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  
