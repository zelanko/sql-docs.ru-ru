---
title: Элемент PermissionSet (ASSL) | Документация Майкрософт
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
- PermissionSet Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PermissionSet
helpviewer_keywords:
- PermissionSet element
ms.assetid: da5a9175-48e4-4b5e-a780-3e0077939974
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 471ef43aea9fadcca7ab8a4a36870a3bdddee22f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263470"
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Safe*|Разрешаются только внутренние вычисления и локальный доступ к данным. Набор разрешений*Safe* является наиболее ограниченным. Код, выполняемый сборкой с разрешениями *Safe* , не может получить доступ к внешним системным ресурсам, таким как файлы, сеть, переменные среды или реестр.|  
|*ExternalAccess*|Набор разрешений*Safe*с дополнительными возможностями для доступа к внешним системным ресурсам, таким как файлы, сети, переменные среды и реестр.|  
|*Неограниченный*|Неограниченный предоставляет сборкам неограниченный доступ к ресурсам, внутренним и внешним [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Код, исполняемый внутри сборки с набором разрешений *Unrestricted* , может вызывать неуправляемый код.|  
  
 Перечисление, соответствующее допустимым значениям элемента `PermissionSet` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.PermissionSet>.  
  
## <a name="see-also"></a>См. также  
 [Тип данных ComAssembly &#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [Элемент Assemblies &#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Элемент Database описания &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Элемент Server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
