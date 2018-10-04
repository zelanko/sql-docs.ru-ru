---
title: Элемент CREATE (DTA) | Документация Майкрософт
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
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2631e08b49e646ae6b96670b11834bcb5b3abf5f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48167216"
---
# <a name="create-element-dta"></a>элемент Create (DTA)
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
|**Родительский элемент**|[Элемент Recommendation &#40;DTA&#41;](recommendation-element-dta.md)|  
|**Дочерние элементы**|[Индекс элемента &#40;DTA&#41;](index-element-dta.md)<br /><br /> `Statistics` Элемент (см. в разделе [схемы XML помощника по настройке ядра СУБД](http://schemas.microsoft.com/sqlserver/) сведения)<br /><br /> `Heap` Элемент (см. в разделе [схемы XML помощника по настройке ядра СУБД](http://schemas.microsoft.com/sqlserver/) сведения)|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент с именем **CreateTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Он используется для создания индексов, статистики и структур кучи для указанной пользователем конфигурации. Не путайте этот элемент `Create` с другими типами, которые можно использовать для создания представлений (`CreateViewType`) секционирования (`CreatePType`). Ссылаться на [схемы XML помощника по настройке ядра СУБД](http://schemas.microsoft.com/sqlserver/) сведения об этих и других `Create` типы элементов.  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
