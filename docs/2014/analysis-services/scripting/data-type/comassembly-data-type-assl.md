---
title: Тип данных ComAssembly (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ComAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ComAssembly
helpviewer_keywords:
- ComAssembly data type
ms.assetid: 23c0f4b3-b6ac-4ec8-9254-74d2f84f5244
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cf05a673de90310563cdc5264f61e2da0952450
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133454"
---
# <a name="comassembly-data-type-assl"></a>Тип данных ComAssembly (ASSL)
  Определяет производный тип данных, представляющий библиотеку COM, связанную с [Server](../objects/server-element-assl.md) или [базы данных](../objects/database-element-assl.md) элемент.  
  
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
|Базовые типы данных|[Сборки](../objects/assembly-element-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Source](../properties/source-element-comassembly-assl.md)|  
|Производные элементы|См. в разделе [сборки](../objects/assembly-element-assl.md) ([сборки](../collections/assemblies-element-assl.md) коллекцию [базы данных](../objects/database-element-assl.md) или [Server](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 `ComAssembly` Элемент содержит ссылку на (полное имя файла или программный идентификатор) в библиотеку COM, связанные с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или с конкретной базой данных экземпляра [!INCLUDE[ssAS](../../../includes/ssas-md.md)].  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ClrAssembly &#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
