---
title: Тип данных ClrAssembly (ASSL) | Документы Microsoft
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
- ClrAssembly Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClrAssembly
helpviewer_keywords:
- ClrAssembly data type
ms.assetid: 3f5dc5a1-ebd6-41b8-ac04-91d4de137eb4
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e17992a5d15113ec0de5dd75978f932cb83d11c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098996"
---
# <a name="clrassembly-data-type-assl"></a>Тип данных ClrAssembly (ASSL)
  Определяет производный тип данных, представляющий [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборку, связанную с [базы данных](../objects/database-element-assl.md) или [сервера](../objects/server-element-assl.md) элемент  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ClrAssembly>  
      <!-- The following elements extend Assembly -->  
   <Files>...</Files>  
      <PermissionSet>...</PermissionSet>  
</ClrAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[сборки](../objects/assembly-element-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|Нет (абстрактный тип)|  
|Дочерние элементы|[Файлы](../collections/files-element-assl.md), [PermissionSet](../properties/permissionset-element-assl.md)|  
|Производные элементы|В разделе [сборки](../objects/assembly-element-assl.md) ([сборки](../collections/assemblies-element-assl.md) коллекцию [базы данных](../objects/database-element-assl.md) или [сервера](../objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Примечания  
 `ClrAssembly` Элемент содержит файлы, необходимые для повторного создания [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборки, связанной с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или с конкретной базой данных экземпляра [!INCLUDE[ssAS](../../../includes/ssas-md.md)], а также разрешения, необходимые для выполнения этой сборки.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ClrAssembly>.  
  
## <a name="see-also"></a>См. также  
 [Файл элемента &#40;ASSL&#41;](../objects/file-element-assl.md)   
 [Тип данных ClrAssemblyFile &#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)   
 [Элемент данных &#40;ASSL&#41;](../objects/data-element-assl.md)   
 [Тип данных DataBlock &#40;ASSL&#41;](datablock-data-type-assl.md)   
 [Блокирует элемент &#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [Блокировать элемент &#40;ASSL&#41;](../objects/block-element-assl.md)   
 [Тип данных ComAssembly &#40;ASSL&#41;](assembly-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  