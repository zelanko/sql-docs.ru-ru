---
title: Тип данных DataBlock (ASSL) | Документы Microsoft
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
- DataBlock Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataBlock
helpviewer_keywords:
- DataBlock data type
ms.assetid: 4192b388-613a-472b-881c-f9c02215aa81
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 12cbd6c1a2723cfc0d9e5b68ff4a484878c82a74
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100096"
---
# <a name="datablock-data-type-assl"></a>Тип данных DataBlock (ASSL)
  Определяет примитивный тип данных, представляющий коллекцию блоков данных, используемых для хранения двоичного содержимого [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataBlock>  
   <Blocks>...</Blocks>  
</DataBlock>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Блоки](../collections/blocks-element-assl.md)|  
|Производные элементы|[Данные](../objects/data-element-assl.md) элемент [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) типа ([файлы](../collections/files-element-assl.md) коллекцию [ClrAssembly](assembly-data-type-assl.md) типа)|  
  
## <a name="see-also"></a>См. также  
 [Элемент Assembly &#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Файл элемента &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Блокировать элемент &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  