---
title: Элемент DTAInput (DTA) | Документация Майкрософт
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
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: da1874685815c46223a4a9e644104012c047d471
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060604"
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
|**Родительский элемент**|[Элемент DTAXML &#40;DTA&#41;](dtaxml-element-dta.md)|  
|**Дочерние элементы**|[Элемент Server &#40;DTA&#41;](server-element-dta.md)<br /><br /> [Элемент Workload &#40;DTA&#41;](workload-element-dta.md)<br /><br /> [Элемент TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)<br /><br /> [Элемент конфигурации &#40;DTA&#41;](configuration-element-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент является корневым в иерархии входной схемы помощника по настройке ядра СУБД. С помощью входных аргументов помощника по настройке ядра СУБД можно задавать серверы с подлежащими настройке базами данных, рабочие нагрузки, параметры настройки или пользовательскую конфигурацию.  
  
## <a name="example"></a>Пример  
 Пример использования элемента **DTAInput** см. в разделе [Образец простого входного файла XML (DTA)](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
