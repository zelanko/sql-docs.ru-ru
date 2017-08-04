---
title: "StrToMember (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRTOMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToMember function
ms.assetid: eb8a3dc0-5ae4-434e-b321-680a81a59e67
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1b87517d73298dbc837d5659ac18b967c45aeaf7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="strtomember-mdx"></a>StrToMember (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает элемент, заданный строкой в формате многомерных выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Name*  
 Допустимое строковое выражение, явно или неявно задающее элемент.  
  
## <a name="remarks"></a>Замечания  
 **StrToMember** функция возвращает элемент, заданный строковым выражением. **StrToMember** функция обычно используется с пользовательскими функциями для возвращения спецификации элемента из внешней функции обратно в инструкцию многомерных Выражений или параметризованный запрос многомерных Выражений.  
  
-   Когда используется флаг CONSTRAINED, имя элемента должно напрямую разрешаться в полное или неполное имя элемента. Этот флаг используется для уменьшения риска атак, использующих вставку инструкций SQL в указанную строку. Если строка, которое не разрешается напрямую в полное или неполное имя элемента, возникает следующая ошибка: «ограничения, установленные флагом CONSTRAINED функции STRTOMEMBER нарушены.»  
  
-   Когда флаг CONSTRAINED не используется, заданный элемент может быть напрямую разрешен в имя элемента или же в допустимое многомерное выражение, возвращающее имя элемента.  
  
-   Дополнительные сведения о различиях между наборами и элементами см. в разделах «Использование выражений наборов» и «Использование выражений элементов».  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает меры Reseller Sales Amount для элемента Bayern в иерархии атрибута State-Province, с помощью **StrToMember** функции. Заданная строка предоставляет полное имя элемента.  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 Следующий пример возвращает меры Reseller Sales Amount для элемента Bayern с помощью **StrToMember** функции. Строка с именем предоставляет только неполное имя элемента, запрос возвращает первый экземпляр заданного элемента, содержащегося в иерархии Customer Geography в измерении Customer, которое не пересекается с измерением Reseller Sales. Для обеспечения ожидаемого результата рекомендуется указывать полное имя.  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 Следующий пример возвращает меры Reseller Sales Amount для элемента Bayern в иерархии атрибута State-Province, с помощью **StrToMember** функции. Строка с именем разрешается в полное имя элемента.  
  
```  
SELECT {StrToMember('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается сообщение об ошибке, поскольку используется флаг CONSTRAINED. Хотя предоставленное имя элемента строки, содержащее допустимое многомерное выражение, возвращает полное имя элемента, из-за флага CONSTRAINED требуется указывать полное или неполное имя элемента в строке имени.  
  
```  
SELECT StrToMember ('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

