---
title: Столбцы сопоставления качества данных (службы DQS), надстройка MDS для Excel | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ecbbaba1441fa150daaecbfcbc7cbdf65636de55
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482640"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>Столбцы сопоставления качества данных (службы DQS), надстройка MDS для Excel
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]после сопоставления данных в группе **Качество данных** на ленте можно нажать кнопку **Показать подробности** , чтобы вывести столбцы с дополнительными сведениями.  
  
 В следующей таблице показаны столбцы, которые отображаются при сопоставлении данных.  
  
|Имя|Описание|  
|----------|-----------------|  
|**CLUSTER_ID**|Уникальный идентификатор, используемый для группировки схожих записей. Все схожие строки имеют одинаковый **CLUSTER_ID**. Если значение **CLUSTER_ID** для строки не отображается, значит схожие записи не были найдены.|  
|**RECORD_ID**|Уникальный идентификатор, используемый для идентификации записей. Аналогичен значению «Код», которое хранится в репозитории MDS. Используется для идентификации записи. Создается автоматически при каждом сопоставлении.|  
|**PIVOT_MARK**|Произвольная запись, с которой сравниваются другие записи. У нее нет значения оценки.|  
|**ПОНЯТЬ**|Отражает, насколько схожи записи в группе с эталонной записью. Эта оценка определяется службами DQS. Если оценка не отображается, это означает либо то, что запись является сводной, либо что совпадения не найдены.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление качества данных в надстройка MDS для Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Сопоставление схожих &#40;данных надстройка MDS для Excel&#41;](match-similar-data-mds-add-in-for-excel.md)   
 [Сопоставление данных](../../data-quality-services/data-matching.md)  
  
  
