---
title: Столбцы сопоставления качества данных (службы DQS), надстройка MDS для Excel | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 79af46616a685d8e52086c3621a963c350db7abf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195203"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>Столбцы сопоставления качества данных (службы DQS), надстройка MDS для Excel
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]после сопоставления данных в группе **Качество данных** на ленте можно нажать кнопку **Показать подробности** , чтобы вывести столбцы с дополнительными сведениями.  
  
 В следующей таблице показаны столбцы, которые отображаются при сопоставлении данных.  
  
|Имя|Описание|  
|----------|-----------------|  
|**CLUSTER_ID**|Уникальный идентификатор, используемый для группировки схожих записей. Все схожие строки имеют одинаковый **CLUSTER_ID**. Если значение **CLUSTER_ID** для строки не отображается, значит схожие записи не были найдены.|  
|**RECORD_ID**|Уникальный идентификатор, используемый для идентификации записей. Аналогичен значению «Код», которое хранится в репозитории MDS. Используется для идентификации записи. Создается автоматически при каждом сопоставлении.|  
|**PIVOT_MARK**|Произвольная запись, с которой сравниваются другие записи. У нее нет значения оценки.|  
|**SCORE**|Отражает, насколько схожи записи в группе с эталонной записью. Эта оценка определяется службами DQS. Если оценка не отображается, это означает либо то, что запись является сводной, либо что совпадения не найдены.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление качества данных в надстройка MDS для Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Сопоставление схожих данных (надстройка MDS для Excel)](match-similar-data-mds-add-in-for-excel.md)   
 [Сопоставление данных](../../data-quality-services/data-matching.md)  
  
  