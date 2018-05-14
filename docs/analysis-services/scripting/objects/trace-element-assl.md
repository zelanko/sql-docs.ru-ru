---
title: Элемент trace (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 603d70f895fa66fc73df33b3f77cf45f10e76d34
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="trace-element-assl"></a>Элемент Trace (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет трассировку, к которой можно отправлять запросы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      Profiler syntax  
<Traces>  
   <Trace>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LogFileName>...</LogFileName>  
      <LogFileAppend>...</LogFileAppend>  
      <LogFileSize>...</LogFileSize>  
      <Audit>...</Audit>  
      <LogFileRollover>...</LogFileRollover>  
      <AutoRestart>...</AutoRestart>  
      <StopTime>...</StopTime>  
      <Filter>...</Filter>  
      <Events>...</Events>  
      <Annotations>...</Annotations>  
   </Trace>  
</Traces>  
```  
  
```  
  
      Extended Events syntax  
<Traces>  
   <Trace>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate> 
      <AutoRestart>...</AutoRestart>
      <XEvent>...</XEvent>  
      <Annotations>...</Annotations>  
   </Trace>  
</Traces>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[трассировки](../../../analysis-services/scripting/collections/traces-element-assl.md)|  
|Дочерние элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md), [аудита](../../../analysis-services/scripting/properties/audit-element-assl.md), [AutoRestart](../../../analysis-services/scripting/properties/autorestart-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [описание](../../../analysis-services/scripting/properties/description-element-assl.md), [события](../../../analysis-services/scripting/collections/events-element-assl.md), [Фильтра](../../../analysis-services/scripting/properties/filter-element-trace-assl.md), [идентификатор](../../../analysis-services/scripting/properties/id-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [LogFileAppend](../../../analysis-services/scripting/properties/logfileappend-element-assl.md), [LogFileName](../../../analysis-services/scripting/properties/logfilename-element-assl.md), [LogFileRollover](../../../analysis-services/scripting/properties/logfilerollover-element-assl.md), [LogFileSize](../../../analysis-services/scripting/properties/logfilesize-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md), [StopTime](../../../analysis-services/scripting/properties/stoptime-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>См. также  
 [Элемент Server & #40; ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
