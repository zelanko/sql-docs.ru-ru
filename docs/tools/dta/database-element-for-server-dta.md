---
title: Элемент Database описания сервера (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f279de19e0a9634011dc84e70c984d948f185bab
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="database-element-for-server-dta"></a>Элемент Database описания сервера (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Позволяет задать базу данных, которую необходимо настроить на конкретном сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|Нет.|  
|Значение по умолчанию|Нет.|  
|Наличие|Требуется один или несколько раз для каждого элемента **Server** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|Родительский элемент|[Элемент Server (DTA)](../../tools/dta/server-element-dta.md)|  
|Дочерние элементы|[Элемент Name для базы данных (DTA)](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Элемент Schema описания базы данных (DTA)](../../tools/dta/schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Этот элемент с именем **DatabaseDetailsTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Не путайте этот элемент **Database** с элементом, корневым родительским элементом которого является **Configuration** . Дополнительные сведения см. в разделе [Элемент Database для конфигурации (DTA)](../../tools/dta/database-element-for-configuration-dta.md).  
  
## <a name="example"></a>Пример  
 Пример использования элемента **Database** см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
