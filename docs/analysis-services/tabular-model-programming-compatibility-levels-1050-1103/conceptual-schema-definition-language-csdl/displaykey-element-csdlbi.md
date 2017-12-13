---
title: "Элемент DisplayKey (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ea38abe670eb7585a8f0b6286f8ffa059d6a4457
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="displaykey-element-csdlbi"></a>Элемент DisplayKey (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Элемент DisplayKey содержит список из следующих элементов, составляющих вместе строгий идентификатор. DisplayKey встречается только как дочерний элемент EntityType. Он может ссылаться на столбцы или окончания роли.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены атрибуты элемента DisplayKey.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|IsDisplayKey|Нет|True или False.|  
  
## <a name="remarks"></a>Замечания  
 Этот элемент предназначен для отчетов. Элемент, к которому применяется этот атрибут, не обязательно должен быть фактическим ключом таблицы, а только лишь элементом, представляемым в виде ключа. Однако столбец, используемый для DisplayKey, должен содержать уникальные значения.  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 приведен столбец из примера модели AdventureWorks, который назначен как DisplayKey для таблицы.  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
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
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Основные понятия CSDLBI](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  
