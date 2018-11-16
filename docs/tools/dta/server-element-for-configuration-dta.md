---
title: Элемент Server описания конфигурации (DTA) | Документация Майкрософт
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
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1374ae2bff41360c473d039909859bd1f67b4f95
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671463"
---
# <a name="server-element-for-configuration-dta"></a>Элемент Server описания конфигурации (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Содержит сведения идентификации сервера, на котором помощник по настройке ядра СУБД должен произвести оценку гипотетической конфигурации (заданной элементом **Configuration** ).  
  
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
|**Наличие**|Требуется один раз на каждый элемент **Configuration** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Configuration (DTA)](../../tools/dta/configuration-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания сервера (DTA)](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Элемент Database описания конфигурации (DTA)](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Вы можете указать только один элемент **Server** для элемента **Configuration** . Этот элемент с именем **ServerTypecomplexType** определен в [схеме XML помощника по настройке ядра СУБД](https://go.microsoft.com/fwlink/?linkid=43100). Не следует путать данный элемент **Server** с дочерним элементом элемента **DTAInput** . Дополнительные сведения см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
