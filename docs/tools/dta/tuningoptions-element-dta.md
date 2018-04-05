---
title: Элемент TuningOptions (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f82d39a90f515d4f70d9e48bef7f20996ba60f78
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="tuningoptions-element-dta"></a>Элемент TuningOptions (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Содержит параметры конкретного сеанса настройки.  
  
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
|**Применяемость**|Необязательно. В случае использования может применяться только один раз для каждого элемента **DTAInput** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAInput &#40; DTA &#41;](../../tools/dta/dtainput-element-dta.md)|  
|**Дочерние элементы**|Элемент**ReportSet** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент**TuningLogTable** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент**NumberOfEvents** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [Элемент TuningTimeInMin &#40; DTA &#41;](../../tools/dta/tuningtimeinmin-element-dta.md)<br /><br /> [Элемент StorageBoundInMB &#40; DTA &#41;](../../tools/dta/storageboundinmb-element-dta.md)<br /><br /> Элемент**MaxKeyColumnsInIndex** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент**MaxColumnsInIndex** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент**MinPercentageImprovement** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100)<br /><br /> [Элемент TestServer &#40; DTA &#41;](../../tools/dta/testserver-element-dta.md)<br /><br /> [Элемент FeatureSet &#40; DTA &#41;](../../tools/dta/featureset-element-dta.md)<br /><br /> [Секционирование элемент &#40; DTA &#41;](../../tools/dta/partitioning-element-dta.md)<br /><br /> [Элемент DropOnlyMode &#40; DTA &#41;](../../tools/dta/droponlymode-element-dta.md)<br /><br /> [Элемент KeepExisting &#40; DTA &#41;](../../tools/dta/keepexisting-element-dta.md)<br /><br /> [Элемент OnlineIndexOperation &#40; DTA &#41;](../../tools/dta/onlineindexoperation-element-dta.md)<br /><br /> [Элемент DatabaseToConnect &#40; DTA &#41;](../../tools/dta/databasetoconnect-element-dta.md)<br /><br /> Элемент**IgnoreConstantsInWorkload** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Элемент**RetainShellDB** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Пример  
 Примеры элемента **TuningOptions** см. в разделе [Образцы входных XML-файлов (DTA)](../../tools/dta/xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
