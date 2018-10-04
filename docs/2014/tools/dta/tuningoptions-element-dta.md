---
title: Элемент TuningOptions (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a4630640d2d61685accdb26031b87aff2883b644
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48065844"
---
# <a name="tuningoptions-element-dta"></a>Элемент TuningOptions (DTA)
  Содержит параметры конкретного сеанса настройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необязательный параметр. Если используется, может использоваться только один раз для каждого `DTAInput` элемент.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAInput &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Дочерние элементы**|`ReportSet` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `TuningLogTable` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `NumberOfEvents` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [Элемент TuningTimeInMin &#40;DTA&#41;](tuningtimeinmin-element-dta.md)<br /><br /> [Элемент StorageBoundInMB &#40;DTA&#41;](storageboundinmb-element-dta.md)<br /><br /> `MaxKeyColumnsInIndex` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MaxColumnsInIndex` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MinPercentageImprovement` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100)<br /><br /> [Элемент TestServer &#40;DTA&#41;](server-element-dta.md)<br /><br /> [Элемент FeatureSet &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Элемент partitioning &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [Элемент DropOnlyMode &#40;DTA&#41;](droponlymode-element-dta.md)<br /><br /> [Элемент KeepExisting &#40;DTA&#41;](keepexisting-element-dta.md)<br /><br /> [Элемент OnlineIndexOperation &#40;DTA&#41;](onlineindexoperation-element-dta.md)<br /><br /> [Элемент DatabaseToConnect &#40;DTA&#41;](databasetoconnect-element-dta.md)<br /><br /> `IgnoreConstantsInWorkload` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `RetainShellDB` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Пример  
 Примеры `TuningOptions` элемент, см. в разделе [образцы входных файлов XML &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
