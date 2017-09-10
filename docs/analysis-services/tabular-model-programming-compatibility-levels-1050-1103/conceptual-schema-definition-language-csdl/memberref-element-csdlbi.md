---
title: "Элемент MemberRef (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3ca4fcb2b59e2a99153ccd55fce93be47a58d961
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="memberref-element-csdlbi"></a>Элемент MemberRef (CSDLBI)
  Элемент MemberRef определяет имя свойства, являющегося целью ссылки.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент MemberRef.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Название|Да|Имя свойства, содержащегося в элементе MemberRef.|  
  
## <a name="memberrefs-element"></a>Элемент MemberRef  
 MemberRef — сложный тип, определяющий коллекцию элементов, где каждый элемент содержится в элементе MemberRef.  
  
 В следующей таблице перечислены элементы и атрибуты типа MemberRefs.  
  
|Название|Обязателен|Описание|  
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
  
## <a name="see-also"></a>См. также:  
 [Технический справочник по заметки бизнес-Аналитики для языка CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
