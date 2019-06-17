---
title: Элемент Server описания конфигурации (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2bc763d621d15f982a2670483683d3862e678c98
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63283678"
---
# <a name="server-element-for-configuration-dta"></a>Элемент Server описания конфигурации (DTA)
  Содержит сведения идентификации сервера, на котором помощник по настройке ядра СУБД должен произвести оценку гипотетической конфигурации (заданной элементом `Configuration`).  
  
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
|**Наличие**|Требуется один раз на каждый элемент `Configuration`.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Configuration (DTA)](configuration-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания сервера (DTA)](name-element-for-server-dta.md)<br /><br /> [Элемент Database описания конфигурации (DTA)](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Можно указать только один `Server` элемент для `Configuration` элемент. Этот элемент с именем **ServerTypecomplexType** определен в [схеме XML помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100). Не следует путать данный элемент `Server` с дочерним элементом элемента `DTAInput`. Дополнительные сведения см. в разделе [Элемент Server (DTA)](server-element-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
