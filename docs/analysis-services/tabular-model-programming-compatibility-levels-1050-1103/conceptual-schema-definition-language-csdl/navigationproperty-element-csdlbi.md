---
title: "Элемент NavigationProperty (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b004e611448db0100186a9f6d7fa9812d3de9c15
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="navigationproperty-element-csdlbi"></a>Элемент NavigationProperty (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Элемент NavigationProperty — сложный тип, который расширяет тип элемента языка CSDL для поддержки навигации в моделях данных бизнес-аналитики.  
  
> [!WARNING]  
>  Этот элемент предназначен для отчетности, поэтому его изменение и управление им не допускаются.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент NavigationProperty.  
  
|Имя|Обязателен|Description|  
|----------|-----------------|-----------------|  
|CollectionCaption|нет|Имя во множественном числе, которым называется набор экземпляров свойства навигации.<br /><br /> Если этот атрибут опускается, используется атрибут Caption базового элемента.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
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
 **Multidimensional**  
  
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
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
