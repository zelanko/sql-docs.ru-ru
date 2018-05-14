---
title: Элемент MemberRef (CSDLBI) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 79b6f2684dabcb45cfddac626bc2a6aa140298f3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="memberref-element-csdlbi"></a>Элемент MemberRef (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 **Табличные**  
  
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
 **Многомерные**  
  
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
  
  
