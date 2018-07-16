---
title: Элемент MemberRef (CSDLBI) | Документация Майкрософт
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
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f308a9c890c36b5948c0f2c8a8468350c2e7cf4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265270"
---
# <a name="memberref-element-csdlbi"></a>Элемент MemberRef (CSDLBI)
  Элемент MemberRef определяет имя свойства, являющегося целью ссылки.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент MemberRef.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Имя|Да|Имя свойства, содержащегося в элементе MemberRef.|  
  
## <a name="memberrefs-element"></a>Элемент MemberRef  
 MemberRef — сложный тип, определяющий коллекцию элементов, где каждый элемент содержится в элементе MemberRef.  
  
 В следующей таблице перечислены элементы и атрибуты типа MemberRefs.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|MemberRef|Да|Значение типа String, содержащее ссылку на элемент.|  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере для CSDLBI версии 1.1 представлена часть образца модели данных AdventureWorks, которая определяет таблицу Products. Здесь элемент MemberRef используется для каждого столбца, включенного в поле, установленное по умолчанию для модели.  
  
```  
  
<bi:EntityType>  
   <bi:DefaultDetails>  
     <bi:MemberRef Name="Color" />  
     <bi:MemberRef Name="DealerPrice" />  
     <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 Следующий пример для CSDLBI версии 1.1 представляет часть куба операций Contoso, определяющую таблицу Bikes. В этом примере элемент MemberRef используется для указания имени столбца, используемого как набор полей по умолчанию для отчетов, а другой элемент MemberRef — для ссылки на столбец, представляющий порядок сортировки.  
  
```  
  
<bi:DefaultDetails>  
   <bi:MemberRef Name="Color" />  
</bi:DefaultDetails>  
  
<bi:SortMembers>  
   <bi:MemberRef Name="Color" />  
</bi:SortMembers>  
  
```  
  
## <a name="see-also"></a>См. также  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
