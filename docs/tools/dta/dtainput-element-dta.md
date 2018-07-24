---
title: Элемент DTAInput (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e5de4ebe29049c40e3fd9b235062854722a1c3ae
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38058565"
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
  
|Характеристики|Описание|  
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
  
  
