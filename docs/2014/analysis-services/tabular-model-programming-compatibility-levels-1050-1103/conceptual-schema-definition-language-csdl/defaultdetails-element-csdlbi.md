---
title: Элемент DefaultDetails (CSDLBI) | Документы Microsoft
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
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 2b10c8b155cb0f06754ed6c2bc45062ae5e69898
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194818"
---
# <a name="defaultdetails-element-csdlbi"></a>Элемент DefaultDetails (CSDLBI)
  Элемент DefaultDetails представляет список ссылок на свойства, которые совместно определяют поле «набор полей по умолчанию» столбцов в таблице. Каждое свойство может ссылаться либо на меру, либо на столбец.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент DefaultDetails.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|Нет|Положительное целое число, которое указывает наличие и позицию в подборке.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 представлен фрагмент данных из примера модели AdventureWorks. Имеется только один набор столбцов по умолчанию для таблицы Employees (Title). Однако для таблицы Products как наборы полей по умолчанию определены три столбца.  
  
```  
  
<EntityType   
    Name="DimEmployee">  
....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Title" />  
   </bi:DefaultDetails>  
.....  
<EntityType   
    Name="Products">  
.....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
      <bi:MemberRef Name="DealerPrice" />  
      <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 В следующем примере для CSDLBI версии 1.1 показан фрагмент из определения таблицы Bike в кубе операций Contoso. Эта заметка указывает, что столбец Color должен отображаться по умолчанию, если не указаны другие столбцы для отображения.  
  
```  
  
<EntityType Name="Bike">  
   <Key>  
   <PropertyRef Name="RowNumber" />  
   </Key>  
....  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
   </bi:DefaultDetails>  
   <bi:SortMembers>  
      <bi:MemberRef Name="Color" />  
   </bi:SortMembers>  
....  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели табличного объекта](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Основные понятия CSDLBI](../csdlbi-concepts.md)  
  
  