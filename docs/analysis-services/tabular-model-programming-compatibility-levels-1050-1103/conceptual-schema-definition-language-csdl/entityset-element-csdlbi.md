---
title: "Элемент EntitySet (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: d4703c9e-5594-472e-a85b-0f5bd0d73d6f
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 93f05510fefc720e074db3fbc26e2347b660031e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="entityset-element-csdlbi"></a>Элемент EntitySet (CSDLBI)
  Элемент EntitySet определяет коллекцию сущностей определенного типа в модели данных CSDLBI.  
  
 В элементе EntitySet должен указываться каждый из типов сущностей, включенных в модель данных. Сведения об этих сущностях в моделях указаны в списке дочерних сущностей этого типа в элементе Entity. Дополнительные сведения см. в разделе [Элемент EntityType (CSDLBI)](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md).  
  
 Свойства, такие как параметры сортировки и язык, определяются на уровне элемента EntityContainer, а не на уровне отдельных объектов. Однако столбцы и текстовые атрибуты в пределах модели могут располагать заголовками или переводами на других языках.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие EntitySet.  
  
|Имя атрибута|Обязателен|Описание|  
|--------------------|-----------------|-----------------|  
|Заголовок|Нет|Понятное описание набора сущностей.|  
|CollectionCaption|Нет|Строка, содержащая имя сущности во множественном числе.|  
|ReferenceName|Нет|Содержит необъединенное, полное имя сущности. В многомерной модели это соответствует имени CubeDimension.|  
|Скрыта|Нет|Указывает, скрыта ли эта сущность. По умолчанию сущности не скрыты.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 приведены определения таблиц Date и Geography из табличной модели AdventureWorks.  
  
```  
  
<EntitySet   
   Name="Date"   
   EntityType="Sandbox. Date">  
<bi:EntitySet />  
</EntitySet>  
  
<EntitySet   
   Name="Geography"   
   EntityType="Sandbox.Geography">  
<bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 В следующем примере для CSDLBI версии 1.1 приведено несколько элементов EntitySet из куба розничных операций Contoso.  
  
```  
  
<EntitySet Name="Outage" EntityType="Sandbox.Outage">  
       <bi:EntitySet />  
</EntitySet>  
  
<EntitySet Name="Store" EntityType="Sandbox.Store">  
     <bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
