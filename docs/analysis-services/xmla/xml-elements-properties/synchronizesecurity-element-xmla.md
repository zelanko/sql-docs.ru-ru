---
title: "Элемент SynchronizeSecurity (XML для Аналитики) | Документы Microsoft"
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
- SynchronizeSecurity Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.synchronizesecurity
- http://schemas.microsoft.com/analysisservices/2003/engine#SynchronizeSecurity
- urn:schemas-microsoft-com:xml-analysis#SynchronizeSecurity
helpviewer_keywords:
- SynchronizeSecurity element
ms.assetid: d37dbb95-f4a4-44ac-8eb9-f661d5bb5018
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 94f58bf16e0127b1686e83a0e81ba754c3cf0066
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="synchronizesecurity-element-xmla"></a>Элемент SynchronizeSecurity (XML для аналитики)
  Указывает, как синхронизировать определения безопасности, такие как роли и разрешения, во время выполнения [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*SkipMembership*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Безопасности** определяет, является ли определения безопасности, такие как роли и разрешения, определенные в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] синхронизацию базы данных во время **синхронизации**  команды. Этот элемент также определяет, включаются ли определенные в качестве элементов определений безопасности учетные записи пользователей и группы Windows в виде части команды **Synchronize** .  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*SkipMembership*|Включает определения безопасности, но исключает сведения о членстве во время выполнения команды **Synchronize** .|  
|*CopyAll*|Включает определения безопасности и сведения о членстве во время выполнения команды **Synchronize** .|  
|*IgnoreSecurity*|Исключает определения безопасности во время выполнения команды **Synchronize** .|  
  
## <a name="see-also"></a>См. также:  
 [Элемент безопасности &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

