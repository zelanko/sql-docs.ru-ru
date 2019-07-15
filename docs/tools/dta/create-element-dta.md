---
title: Элемент CREATE (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bd566edd70ae2b7cd5fd5175a64b6a09c793194d
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67730952"
---
# <a name="create-element-dta"></a>элемент Create (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Содержит сведения об индексах, статистике или структурах кучи в указанной пользователем конфигурации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Данный элемент должен быть указан один раз для каждого типа структур физического проектирования (индексов, статистики или структур кучи).|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Recommendation (DTA)](../../tools/dta/recommendation-element-dta.md)|  
|**Дочерние элементы**|[Элемент Index (DTA)](../../tools/dta/index-element-dta.md)<br /><br /> Элемент**Statistics** (см. раздел [XML-схема помощника по настройке ядра СУБД](https://schemas.microsoft.com/sqlserver/) )<br /><br /> Элемент**Heap** (см. раздел [XML-схема помощника по настройке ядра СУБД](https://schemas.microsoft.com/sqlserver/) )|  
  
## <a name="remarks"></a>Remarks  
 Этот элемент с именем **CreateTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Он используется для создания индексов, статистики и структур кучи для указанной пользователем конфигурации. Не путайте этот элемент **Create** с другими типами, которые можно использовать для создания представлений (**CreateViewType**) или секционирования (**CreatePType**). Дополнительные сведения об этих и других типах элемента [Create](https://schemas.microsoft.com/sqlserver/) см. в разделе **XML-схема помощника по настройке ядра СУБД** .  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
