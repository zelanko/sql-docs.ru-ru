---
title: Элемент EntitySet (CSDLBI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: d4703c9e-5594-472e-a85b-0f5bd0d73d6f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dabe6cf0748f220fcef7bfb9b2577426c7ff65a2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091634"
---
# <a name="entityset-element-csdlbi"></a>Элемент EntitySet (CSDLBI)
  Элемент EntitySet определяет коллекцию сущностей определенного типа в модели данных CSDLBI.  
  
 В элементе EntitySet должен указываться каждый из типов сущностей, включенных в модель данных. Сведения об этих сущностях в моделях указаны в списке дочерних сущностей этого типа в элементе Entity. Дополнительные сведения см. в разделе [Элемент EntityType (CSDLBI)](entitytype-element-csdlbi.md).  
  
 Свойства, такие как параметры сортировки и язык, определяются на уровне элемента EntityContainer, а не на уровне отдельных объектов. Однако столбцы и текстовые атрибуты в пределах модели могут располагать заголовками или переводами на других языках.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие EntitySet.  
  
|Имя атрибута|Обязателен|Описание|  
|--------------------|-----------------|-----------------|  
|Заголовок|Нет|Понятное описание набора сущностей.|  
|CollectionCaption|Нет|Строка, содержащая имя сущности во множественном числе.|  
|ReferenceName|Нет|Содержит необъединенное, полное имя сущности. В многомерной модели это соответствует имени CubeDimension.|  
|Скрытый|Нет|Указывает, скрыта ли эта сущность. По умолчанию сущности не скрыты.|  
  
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
  
## <a name="see-also"></a>См. также  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
