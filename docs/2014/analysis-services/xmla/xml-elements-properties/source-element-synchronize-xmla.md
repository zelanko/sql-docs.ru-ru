---
title: Элемент Source (Synchronize) (XMLA) | Документы Microsoft
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
- Source Element (Synchronize)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Source
- http://schemas.microsoft.com/analysisservices/2003/engine#Source
- microsoft.xml.analysis.source
helpviewer_keywords:
- Source element
ms.assetid: 0a857f91-771f-4c5e-8bf7-4bf17442d4df
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5341a6c993c6053dbe6716dcfcd5155f81a4ae0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193436"
---
# <a name="source-element-synchronize-xmla"></a>Элемент Source (Synchronize) (XML для аналитики)
  Представляет исходную базу данных для целевой базы данных во время синхронизации [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Synchronize>  
   <Source>  
      <Object>...</Object>  
      <ConnectionString>...</ConnectionString>  
   </Source>  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Synchronize](../xml-elements-commands/synchronize-element-xmla.md)|  
|Дочерние элементы|[ConnectionString](connectionstring-element-xmla.md), [объекта](object-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 `Synchronize` Команда использует `Source` установить соединение и определить базу данных на экземпляр элемента [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с которыми необходимо синхронизировать целевую базу данных.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  