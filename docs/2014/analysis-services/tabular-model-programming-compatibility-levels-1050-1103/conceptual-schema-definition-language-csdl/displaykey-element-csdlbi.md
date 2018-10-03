---
title: Элемент DisplayKey (CSDLBI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 929529214979c2c8bd6c441914ef84974a86a807
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060034"
---
# <a name="displaykey-element-csdlbi"></a>Элемент DisplayKey (CSDLBI)
  Элемент DisplayKey содержит следующий список элементов, составляющих вместе строгий идентификатор. DisplayKey встречается только как дочерний элемент EntityType. Он может ссылаться на столбцы или окончания роли.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены атрибуты элемента DisplayKey.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|IsDisplayKey|Нет|True или False.|  
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели табличного объекта](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Основные понятия CSDLBI](../csdlbi-concepts.md)  
  
  
