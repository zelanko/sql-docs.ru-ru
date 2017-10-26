---
title: "Элемент PermissionSet (ASSL) | Документы Microsoft"
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
- PermissionSet Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- PermissionSet
helpviewer_keywords:
- PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d1448c3db59f149697fa429e6d122d9d20fd403f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="permissionset-element-assl"></a>Элемент PermissionSet (ASSL)
  Определяет набор разрешений, связанных с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] сборки .NET Framework.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ClrAssembly>  
   ...  
   <PermissionSet>...</PermissionSet>  
  
</ClrAssembly>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Safe*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Safe*|Разрешаются только внутренние вычисления и локальный доступ к данным. Набор разрешений*Safe* является наиболее ограниченным. Код, выполняемый сборкой с разрешениями *Safe* , не может получить доступ к внешним системным ресурсам, таким как файлы, сеть, переменные среды или реестр.|  
|*ExternalAccess*|Набор разрешений*Safe*с дополнительными возможностями для доступа к внешним системным ресурсам, таким как файлы, сети, переменные среды и реестр.|  
|*Без ограничений*|Неограниченный предоставляет сборкам неограниченный доступ к ресурсам как внутри, так и за пределами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Код, исполняемый внутри сборки с набором разрешений *Unrestricted* , может вызывать неуправляемый код.|  
  
 Перечисление, соответствующее разрешенным значениям для **PermissionSet** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.PermissionSet>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных ComAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Элемент Assemblies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Элемент Database &#40; ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Элемент Server &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

