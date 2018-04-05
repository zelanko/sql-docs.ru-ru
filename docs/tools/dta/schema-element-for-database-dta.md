---
title: Элемент schema описания базы данных (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
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
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2b4da3d22c91ad05ba53736eb17a2210b0c0b5d
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="schema-element-for-database-dta"></a>Элемент Schema описания базы данных (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Указывает схему базы данных, которую необходимо настроить.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для элемента **Database** , указанного в элементе **Server** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Database описания сервера &#40; DTA &#41;](../../tools/dta/database-element-for-server-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания схемы &#40; DTA &#41;](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [Элемент TABLE описания схемы &#40; DTA &#41;](../../tools/dta/table-element-for-schema-dta.md)|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
