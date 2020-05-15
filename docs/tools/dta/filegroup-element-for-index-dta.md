---
title: Элемент Filegroup описания индекса (DTA)
description: В программе dta элемент Filegroup для индекса определяет группу файлов, по которой будет создан индекс в пользовательской конфигурации.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Filegroup element [DTA]
ms.assetid: 7078d2fb-fa77-44fc-beb3-c095088fcb85
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 0b3c331a11cb01807c6193147ca89f3989d26e0d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826480"
---
# <a name="filegroup-element-for-index-dta"></a>Элемент Filegroup описания индекса (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Определяет группу файлов, по которой будет создан индекс в пользовательской конфигурации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Index>  
  <Name>...</Name>  
  <Column>  
    <Name>...</Name>  
  <Filegroup>...</Filegroup>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необязательный параметр. Может использоваться один раз для каждого элемента **Index** . Этот элемент нельзя использовать, если для элемента **PartitionScheme** определены элементы **PartitionColumn** и **Index** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Index (DTA)](../../tools/dta/index-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
