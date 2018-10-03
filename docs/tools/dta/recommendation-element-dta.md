---
title: Элемент Recommendation (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 93846b95297891ae755270e8b23ac9d891be713b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620502"
---
# <a name="recommendation-element-dta"></a>Элемент Recommendation (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Содержит данные о гипотетических индексах, являющихся частью пользовательской конфигурации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необязательный параметр. Может использоваться один раз для каждого элемента **Table** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Table описания схемы (DTA)](../../tools/dta/table-element-for-schema-dta.md)|  
|**Дочерние элементы**|[Элемент Create (DTA)](../../tools/dta/create-element-dta.md)<br /><br /> Элемент**Drop** . Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="remarks"></a>Remarks  
 Этот элемент с именем **RecommendationTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Он используется для задания индексов в гипотетической конфигурации. Не путайте этот элемент **Рекомендация** с другими типами, которые могут использоваться для настройки секционирования (**RecommendationPType**) или представлений (**RecommendationViewType**). Дополнительные сведения об этих и других типах элементов **Recommendation** см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
