---
title: Тип данных ASSEMBLY (ASSL) | Документы Microsoft
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
api_name:
- Assembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Assembly data type
ms.assetid: 0a381322-9509-4579-a754-c6cdd0a70cc9
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3fd706974b0cb4a897a7ef75e147dcd35ac91481
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187821"
---
# <a name="assembly-data-type-assl"></a>Тип данных Assembly (ASSL)
  Определяет абстрактный примитивный тип данных, представляющий [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборку или библиотеку динамической компоновки COM (DLL), связанную с [сервера](../objects/server-element-assl.md) или [базы данных](../objects/database-element-assl.md) элемента.  
  
> [!IMPORTANT]  
>  Использование сборок COM может представлять угрозу безопасности. По этой причине, а также по ряду других сборки COM в службах [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]являются устаревшими. Поддержка сборок COM в последующих версиях может быть прекращена.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Assembly>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <ImpersonationInfo>...</ImpersonationInfo>  
   <Annotations>...</Annotations>  
</Assembly>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[ClrAssembly](assembly-data-type-assl.md), [ComAssembly](comassembly-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [описание](../properties/description-element-assl.md), [идентификатор](../properties/id-element-assl.md), [ImpersonationInfo](../properties/impersonationinfo-element-assl.md), [ LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [имя](../properties/name-element-assl.md)|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Тип данных `Assembly` служит базовым типом данных для элемента `ComAssembly`, представляющего библиотеки COM, связанные с экземпляром или базой данных, и элемент `ClrAssembly`, который представляет сборки платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], связанные с экземпляром или базой данных. Дополнительные сведения о сборках см. в разделе [Управление сборками многомерной модели](../../multidimensional-models/multidimensional-model-assemblies-management.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Assembly>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Элемент Database &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  