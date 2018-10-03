---
title: Элемент MemberRef (CSDLBI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bb0912afd99c7a4859ca4750a3ba1b66fdecd5f5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205723"
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
  
  
