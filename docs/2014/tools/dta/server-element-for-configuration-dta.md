---
title: Элемент Server описания конфигурации (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 131885c5e9547767dece2240bcbd64c06b5e4a61
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087067"
---
# <a name="server-element-for-configuration-dta"></a>Элемент Server описания конфигурации (DTA)
  Содержит сведения идентификации сервера, где будет помощник по настройке ядра СУБД должен произвести оценку гипотетической конфигурации (заданные `Configuration` элемент).  
  
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
|**Дочерние элементы**|[Имя элемента для сервера &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Элемент Database описания конфигурации &#40;DTA&#41;](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Можно указать только один `Server` элемент для `Configuration` элемента. Этот элемент с именем **ServerTypecomplexType** определен в [схеме XML помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100). Не путайте этот `Server` элемент с элементом, который является дочерним объектом `DTAInput` элемента. Дополнительные сведения см. в разделе [Элемент Server (DTA)](server-element-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  