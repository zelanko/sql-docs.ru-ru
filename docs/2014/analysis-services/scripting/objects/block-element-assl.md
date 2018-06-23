---
title: Блокировать элемент (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Block Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Block
helpviewer_keywords:
- Block element
ms.assetid: f45c32ae-e4e0-465a-9564-9ccfb10a858f
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e382ba38c41bc68b3d49b0397cdc3fe3f2dcf0ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187810"
---
# <a name="block-element-assl"></a>Элемент Block (ASSL)
  Содержит все или часть двоичного содержимого [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) элемента.  
  
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
|Родительские элементы|[Блоки](../collections/blocks-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="see-also"></a>См. также  
 [Элемент Assembly &#40;ASSL&#41;](assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Файлы элемент &#40;ASSL&#41;](../collections/files-element-assl.md)   
 [Файл элемента &#40;ASSL&#41;](file-element-assl.md)   
 [Тип данных ClrAssemblyFile &#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [Элемент данных &#40;ASSL&#41;](data-element-assl.md)   
 [Тип данных DataBlock &#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  