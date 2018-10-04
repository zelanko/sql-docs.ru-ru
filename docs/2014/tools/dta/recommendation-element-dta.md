---
title: Элемент Recommendation (DTA) | Документация Майкрософт
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
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 60bc8c4cbd2166a302a0f61176fa198787575f88
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107073"
---
# <a name="recommendation-element-dta"></a>Элемент Recommendation (DTA)
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
|**Наличие**|Необязательный параметр. Может использоваться один раз для каждого `Table` элемент.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент таблицы для схемы &#40;DTA&#41;](table-element-for-schema-dta.md)|  
|**Дочерние элементы**|[Создать элемент &#40;DTA&#41;](create-element-dta.md)<br /><br /> `Drop` элемент. Дополнительные сведения см. в статье [XML-схема помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент с именем **RecommendationTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Он используется для задания индексов в гипотетической конфигурации. Не путайте этот `Recommendation` элемента с другими типами, которые могут использоваться для задания секционирования (`RecommendationPType`) или представлений (`RecommendationViewType`). Сведения об этих и других `Recommendation` типы элементов, см. в разделе [схемы XML помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100).  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
