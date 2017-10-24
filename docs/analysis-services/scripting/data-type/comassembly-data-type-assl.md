---
title: "Тип данных ComAssembly (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ComAssembly Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ComAssembly
helpviewer_keywords:
- ComAssembly data type
ms.assetid: 23c0f4b3-b6ac-4ec8-9254-74d2f84f5244
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e519b7f204e5fe258222a48161dc9032ccc826ac
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="comassembly-data-type-assl"></a>Тип данных ComAssembly (ASSL)
  Определяет производный тип данных, представляющий библиотеку COM, связанную с [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) или [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.  
  
> [!IMPORTANT]  
>  Использование сборок COM может представлять угрозу безопасности. По этой причине, а также по ряду других сборки COM в службах [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]являются устаревшими. Поддержка сборок COM в последующих версиях может быть прекращена.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ComAssembly>  
      <!-- The following elements extend Assembly -->  
   <Source>...</Source>  
</ComAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Сборки](../../../analysis-services/scripting/objects/assembly-element-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Source](../../../analysis-services/scripting/properties/source-element-comassembly-assl.md)|  
|Производные элементы|В разделе [сборки](../../../analysis-services/scripting/objects/assembly-element-assl.md) ([сборки](../../../analysis-services/scripting/collections/assemblies-element-assl.md) коллекцию [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) или [сервера](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 **ComAssembly** элемент содержит ссылку на (полное имя файла или программный идентификатор) в библиотеку COM, связанные с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или с определенным базы данных на экземпляре [!INCLUDE[ssAS](../../../includes/ssas-md.md)].  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных ClrAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

