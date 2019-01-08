---
title: Элемент TuningOptions (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3050ce285cc98386f6de6278bedd2520cb39ba36
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348754"
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
|**Наличие**|Необязательный. В случае использования может применяться только один раз для каждого элемента `DTAInput`.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAInput (DTA)](dtainput-element-dta.md)|  
|**Дочерние элементы**|Элемент `ReportSet`. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент `TuningLogTable`. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент `NumberOfEvents`. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [Элемент TuningTimeInMin (DTA)](tuningtimeinmin-element-dta.md)<br /><br /> [Элемент StorageBoundInMB (DTA)](storageboundinmb-element-dta.md)<br /><br /> Элемент `MaxKeyColumnsInIndex`. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент `MaxColumnsInIndex`. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент `MinPercentageImprovement`. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100)<br /><br /> [Элемент TestServer (DTA)](server-element-dta.md)<br /><br /> [Элемент FeatureSet (DTA)](featureset-element-dta.md)<br /><br /> [Элемент Partitioning (DTA)](partitioning-element-dta.md)<br /><br /> [Элемент DropOnlyMode (DTA)](droponlymode-element-dta.md)<br /><br /> [Элемент KeepExisting (DTA)](keepexisting-element-dta.md)<br /><br /> [Элемент OnlineIndexOperation (DTA)](onlineindexoperation-element-dta.md)<br /><br /> [Элемент DatabaseToConnect (DTA)](databasetoconnect-element-dta.md)<br /><br /> Элемент `IgnoreConstantsInWorkload`. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент `RetainShellDB`. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Пример  
 Примеры `TuningOptions` элемент, см. в разделе [образцы входных файлов XML &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
