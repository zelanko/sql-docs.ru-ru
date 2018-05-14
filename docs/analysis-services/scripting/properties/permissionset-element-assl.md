---
title: Элемент PermissionSet (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2299f76822ae24eb2fee1085fc49836704ba275a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="permissionset-element-assl"></a>Элемент PermissionSet (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Значение по умолчанию|*Безопасный*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Безопасный*|Разрешаются только внутренние вычисления и локальный доступ к данным. Набор разрешений*Safe* является наиболее ограниченным. Код, выполняемый сборкой с разрешениями *Safe* , не может получить доступ к внешним системным ресурсам, таким как файлы, сеть, переменные среды или реестр.|  
|*ExternalAccess*|Набор разрешений*Safe*с дополнительными возможностями для доступа к внешним системным ресурсам, таким как файлы, сети, переменные среды и реестр.|  
|*Без ограничений*|Неограниченный предоставляет сборкам неограниченный доступ к ресурсам как внутри, так и за пределами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Код, исполняемый внутри сборки с набором разрешений *Unrestricted* , может вызывать неуправляемый код.|  
  
 Перечисление, соответствующее разрешенным значениям для **PermissionSet** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.PermissionSet>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ComAssembly & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Элемент Database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Элемент Server & #40; ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
