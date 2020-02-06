---
title: Элемент DTAInput (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 6801f3d8ce45ba41d24d1062ad9979e80e76b38a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307710"
---
# <a name="dtainput-element-dta"></a>Элемент DTAInput (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Содержит определение входных XML-данных для помощника по настройке ядра СУБД.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристики|Description|  
|---------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Может быть при необходимости указан один раз для каждого элемента **DTAXML** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAXML (DTA)](../../tools/dta/dtaxml-element-dta.md)|  
|**Дочерние элементы**|[Элемент Server (DTA)](../../tools/dta/server-element-dta.md)<br /><br /> [Элемент Workload (DTA)](../../tools/dta/workload-element-dta.md)<br /><br /> [Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Элемент Configuration (DTA)](../../tools/dta/configuration-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Этот элемент является корневым в иерархии входной схемы помощника по настройке ядра СУБД. С помощью входных аргументов помощника по настройке ядра СУБД можно задавать серверы с подлежащими настройке базами данных, рабочие нагрузки, параметры настройки или пользовательскую конфигурацию.  
  
## <a name="example"></a>Пример  
 Пример использования элемента **DTAInput** см. в разделе [Образец простого входного файла XML (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
