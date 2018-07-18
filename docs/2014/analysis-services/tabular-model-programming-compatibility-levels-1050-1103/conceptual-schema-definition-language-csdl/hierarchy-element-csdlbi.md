---
title: Элемент Hierarchy (CSDLBI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9debb638-1b28-401b-9499-8f63943863e9
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: be67c3059f09beefae68d0264fd0316579344d64
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250794"
---
# <a name="hierarchy-element-csdlbi"></a>Элемент Hierarchy (CSDLBI)
  Элемент Hierarchy — логический контейнер для полей таблицы, который можно соединить друг с другом в некоторого вида иерархическую структуру. Элемент Hierarchy является производным элемента языка CSDL Member и расширен так, чтобы поддерживать иерархии, созданные в моделях данных бизнес-аналитики.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент Hierarchy  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Документация|Нет|Описание иерархии.|  
|Level|Да|Один или несколько элементов Level, определяющих столбцы, участвующие в иерархии.<br /><br /> См. раздел [Элемент Level (CSDLBI)](level-element-csdlbi.md).|  
  
## <a name="remarks"></a>Примечания  
 В табличных моделях иерархии создаются за счет определения отношений «родитель-потомок» между столбцами одной таблицы. Дополнительные сведения см. в разделе [Иерархии (табличные службы SSAS)](../../tabular-models/hierarchies-ssas-tabular.md).  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
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
 **Multidimensional**  
  
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
 [Общие сведения о модели табличного объекта](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Общие сведения о функциях для иерархий родители потомки в DAX](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [Настройка &#40;все&#41; уровне для иерархий атрибутов](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
