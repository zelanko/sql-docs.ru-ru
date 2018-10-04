---
title: Элемент Server описания конфигурации (DTA) | Документация Майкрософт
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
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10a8fa9eed7f89d9706ab3388eccc881b165ef74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206914"
---
# <a name="server-element-for-configuration-dta"></a>Элемент Server описания конфигурации (DTA)
  Содержит сведения идентификации сервера, в которой помощник по настройке ядра СУБД должен произвести оценку гипотетической конфигурации (определяется `Configuration` элемент).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз на `Configuration` элемент.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент конфигурации &#40;DTA&#41;](configuration-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name для Server &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Элемент Database описания конфигурации &#40;DTA&#41;](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Можно указать только один `Server` элемент для `Configuration` элемент. Этот элемент с именем **ServerTypecomplexType** определен в [схеме XML помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100). Не путайте этот `Server` с элементом, который является дочерним объектом `DTAInput` элемент. Дополнительные сведения см. в разделе [Элемент Server (DTA)](server-element-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
