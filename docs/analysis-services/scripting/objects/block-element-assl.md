---
title: Блокировать элемент (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Block Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Block
helpviewer_keywords:
- Block element
ms.assetid: f45c32ae-e4e0-465a-9564-9ccfb10a858f
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ec3d8d8616d6561e3b7d7e898e6c05d77839e34d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="block-element-assl"></a>Элемент Block (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит все или часть двоичного содержимого [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Blocks>  
   <Block>...</Block>  
</Blocks>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Base64Binary|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Блоки](../../../analysis-services/scripting/collections/blocks-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="see-also"></a>См. также  
 [Элемент Assembly & #40; ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [Элемент файла & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Тип данных ClrAssemblyFile & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [Элемент данных & #40; ASSL & #41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Тип данных DataBlock & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
