---
title: Элемент NavigationProperty (CSDLBI) | Документы Microsoft
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
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
caps.latest.revision: 9
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: bc9940ccc136e8b6934efc9cc25526959cec667f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189349"
---
# <a name="navigationproperty-element-csdlbi"></a>Элемент NavigationProperty (CSDLBI)
  Элемент NavigationProperty — сложный тип, который расширяет тип элемента языка CSDL для поддержки навигации в моделях данных бизнес-аналитики.  
  
> [!WARNING]  
>  Этот элемент предназначен для отчетности, поэтому его изменение и управление им не допускаются.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент NavigationProperty.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|CollectionCaption|Нет|Имя во множественном числе, которым называется набор экземпляров свойства навигации.<br /><br /> Если этот атрибут опускается, используется атрибут Caption базового элемента.|  
  
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
  
## <a name="see-also"></a>См. также  
 [Основные сведения о табличной объектной модели](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  