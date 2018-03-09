---
title: "Столбцы сопоставления качества данных (службы DQS), надстройка MDS для Excel | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: microsoft-excel-add-in
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a09a0bcf2136a01545450932623df419c9726250
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>Столбцы сопоставления качества данных (службы DQS), надстройка MDS для Excel
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]после сопоставления данных в группе **Качество данных** на ленте можно нажать кнопку **Показать подробности** , чтобы вывести столбцы с дополнительными сведениями.  
  
 В следующей таблице показаны столбцы, которые отображаются при сопоставлении данных.  
  
|Имя|Description|  
|----------|-----------------|  
|**CLUSTER_ID**|Уникальный идентификатор, используемый для группировки схожих записей. Все схожие строки имеют одинаковый **CLUSTER_ID**. Если значение **CLUSTER_ID** для строки не отображается, значит схожие записи не были найдены.|  
|**RECORD_ID**|Уникальный идентификатор, используемый для идентификации записей. Аналогичен значению «Код», которое хранится в репозитории MDS. Используется для идентификации записи. Создается автоматически при каждом сопоставлении.|  
|**PIVOT_MARK**|Произвольная запись, с которой сравниваются другие записи. У нее нет значения оценки.|  
|**SCORE**|Отражает, насколько схожи записи в группе с эталонной записью. Эта оценка определяется службами DQS. Если оценка не отображается, это означает либо то, что запись является сводной, либо что совпадения не найдены.|  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление качества данных в надстройке MDS для Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Сопоставление схожих данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)   
 [Сопоставление данных](../../data-quality-services/data-matching.md)  
  
  
