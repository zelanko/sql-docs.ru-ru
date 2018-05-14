---
title: Тип данных ComAssembly (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b01a29856bf42d275b1c4d59c9041a9f6f4ab270
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="comassembly-data-type-assl"></a>Тип данных ComAssembly (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет производный тип данных, представляющий библиотеку COM, связанную с элементом [Server](../../../analysis-services/scripting/objects/server-element-assl.md) или [Database](../../../analysis-services/scripting/objects/database-element-assl.md) .  
  
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
|Производные элементы|См. [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md) (коллекция[Assemblies](../../../analysis-services/scripting/collections/assemblies-element-assl.md) элементов [Database](../../../analysis-services/scripting/objects/database-element-assl.md) или [Server](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 **ComAssembly** элемент содержит ссылку на (полное имя файла или программный идентификатор) в библиотеку COM, связанные с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или с определенным базы данных на экземпляре [!INCLUDE[ssAS](../../../includes/ssas-md.md)].  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ClrAssembly &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
