---
title: Элемент NavigationProperty (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 769e0e59ffe276d606188d7ac432b7e16205607c
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2018
---
# <a name="navigationproperty-element-csdlbi"></a>Элемент NavigationProperty (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Элемент NavigationProperty — сложный тип, который расширяет тип элемента языка CSDL для поддержки навигации в моделях данных бизнес-аналитики.  
  
> [!WARNING]  
>  Этот элемент предназначен для отчетности, поэтому его изменение и управление им не допускаются.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент NavigationProperty.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|CollectionCaption|Нет|Имя во множественном числе, которым называется набор экземпляров свойства навигации.<br /><br /> Если этот атрибут опускается, используется атрибут Caption базового элемента.|  
  
## <a name="example"></a>Пример  
 **Табличные**  
  
 В следующем примере рассмотрено свойство навигации в CSDLBI версии 1.1, в котором описывается связь между таблицей "Product SubCategory" и таблицей "Product" в табличной модели.  
  
```  
  
<NavigationProperty   
    Name="Product_Sub_Category_ProductSubcategoryKey"      
    Relationship="Sandbox.Product_Product_Sub_Category_Product_Sub_Category_ProductSubcategoryKey"  
     FromRole="Product_ProductSubcategoryKey"   
    ToRole="Product_Sub_Category_ProductSubcategoryKey">  
<bi:NavigationProperty   
     ReferenceName="Product Sub-Category_ProductSubcategoryKey" />  
</NavigationProperty>  
```  
  
## <a name="example"></a>Пример  
 **Многомерные**  
  
 В следующем примере показано свойство навигации в CSDLBI версии 1.1, описывающее связь между двумя таблицами в кубе операций Contoso. Связь соединяет таблицы "Bike Category" и "Product Subcategory".  
  
```  
  
<NavigationProperty   
     Name="BikeSubcategory_ProductSubcategoryKey"   
     Relationship="Sandbox.Bike_BikeSubcategory_BikeSubcategory_ProductSubcategoryKey"   
     FromRole="Bike_ProductSubcategoryKey"   
     ToRole="BikeSubcategory_ProductSubcategoryKey">  
   <bi:NavigationProperty />  
</NavigationProperty>  
```  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
