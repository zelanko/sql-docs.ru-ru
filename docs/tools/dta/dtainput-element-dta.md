---
title: "Элемент DTAInput (DTA) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 22a7b07a5dee4e826d2b438d384d44796ca23480
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="dtainput-element-dta"></a>Элемент DTAInput (DTA)
  Содержит определение входных XML-данных для помощника по настройке ядра СУБД.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристики|Описание|  
|---------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Может быть при необходимости указан один раз для каждого элемента **DTAXML** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAXML &#40; DTA &#41;](../../tools/dta/dtaxml-element-dta.md)|  
|**Дочерние элементы**|[Элемент Server &#40; DTA &#41;](../../tools/dta/server-element-dta.md)<br /><br /> [Элемент Workload &#40; DTA &#41;](../../tools/dta/workload-element-dta.md)<br /><br /> [Элемент TuningOptions &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Элемент конфигурации &#40; DTA &#41;](../../tools/dta/configuration-element-dta.md)|  
  
## <a name="remarks"></a>Замечания  
 Этот элемент является корневым в иерархии входной схемы помощника по настройке ядра СУБД. С помощью входных аргументов помощника по настройке ядра СУБД можно задавать серверы с подлежащими настройке базами данных, рабочие нагрузки, параметры настройки или пользовательскую конфигурацию.  
  
## <a name="example"></a>Пример  
 Пример использования элемента **DTAInput** см. в разделе [Образец простого входного файла XML (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

