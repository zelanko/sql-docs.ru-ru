---
title: Столбцы сопоставления качества данных (службы DQS), надстройка MDS для Excel | Документы Майкрософт
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 98613580c3c76016c27360c7d6868f5fe15c42ce
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35328898"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>Столбцы сопоставления качества данных (службы DQS), надстройка MDS для Excel

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]после сопоставления данных в группе **Качество данных** на ленте можно нажать кнопку **Показать подробности** , чтобы вывести столбцы с дополнительными сведениями.  
  
 В следующей таблице показаны столбцы, которые отображаются при сопоставлении данных.  
  
|Имя|Описание|  
|----------|-----------------|  
|**CLUSTER_ID**|Уникальный идентификатор, используемый для группировки схожих записей. Все схожие строки имеют одинаковый **CLUSTER_ID**. Если значение **CLUSTER_ID** для строки не отображается, значит схожие записи не были найдены.|  
|**RECORD_ID**|Уникальный идентификатор, используемый для идентификации записей. Аналогичен значению «Код», которое хранится в репозитории MDS. Используется для идентификации записи. Создается автоматически при каждом сопоставлении.|  
|**PIVOT_MARK**|Произвольная запись, с которой сравниваются другие записи. У нее нет значения оценки.|  
|**SCORE**|Отражает, насколько схожи записи в группе с эталонной записью. Эта оценка определяется службами DQS. Если оценка не отображается, это означает либо то, что запись является сводной, либо что совпадения не найдены.|  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление качества данных в надстройке MDS для Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Сопоставление схожих данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)   
 [Сопоставление данных](../../data-quality-services/data-matching.md)  
  
  
