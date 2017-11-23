---
title: "SELECT INTO (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT
- SELECT_INTO
- SELECT INTO
dev_langs: DMX
helpviewer_keywords:
- mining models [Analysis Services], copying
- SELECT INTO statement
- mining models [Analysis Services], creating
- copying mining models
ms.assetid: 31ab9b4c-e20d-41ee-886f-6665c22c6ad5
caps.latest.revision: "42"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 978c1deca02aa60a7a123707de9ac3e95cd68851
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="select-into-dmx"></a>SELECT INTO (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Создает новую модель интеллектуального анализа данных на основе структуры интеллектуального анализа данных существующей модели. **SELECT INTO** инструкция создает новые модели интеллектуального анализа данных путем копирования схемы и других данных, не относящейся к конкретному алгоритму.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT INTO <new model>   
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH[,] [FILTER(<expression>)]]  
FROM <existing model>  
```  
  
## <a name="arguments"></a>Аргументы  
 *Новая модель*  
 Уникальное имя для новой создаваемой модели.  
  
 *алгоритм*  
 Имя алгоритма интеллектуального анализа данных, определенное поставщиком.  
  
 *список параметров*  
 Необязательно. Список параметров, определенных поставщиком для алгоритма и разделенный запятыми.  
  
 *expression*  
 Выражение, значением которого является действительное условие фильтрации для обучающих данных. Дополнительные сведения о выражениях, которые могут использоваться в качестве фильтров см. в разделе [фильтров для модели интеллектуального анализа данных &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41; ](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 *существующей модели*  
 Имя существующей модели для копирования.  
  
## <a name="remarks"></a>Замечания  
 Если существующая модель является обученной, новая модель автоматически обрабатывается при выполнении этой инструкции. В противном случае новая модель оставляется необработанной.  
  
 **SELECT INTO** инструкция работает только в том случае, если структура существующей модели совместима с алгоритмом новой модели. Следовательно, эта инструкция больше всего подходит для быстрого создания и тестирования моделей, основанных на одном алгоритме. Если изменить тип алгоритма, новый алгоритм должен поддерживать тип данных каждого столбца существующей модели, иначе при обработке модели может произойти ошибка.  
  
 **WITH DRILLTHROUGH** предложение включает детализацию для новой модели интеллектуального анализа данных. Включить детализацию можно только при создании модели.  
  
## <a name="example-1-altering-the-parameters-of-the-model"></a>Пример 1: Изменение параметров модели  
 В следующем примере создается новый модели интеллектуального анализа данных, в зависимости от существующей модели интеллектуального анализа данных, `TM_Clustering`, который создан на [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). В новой модели параметр CLUSTER_COUNT изменяется так, чтобы существовало максимум пять кластеров. В существующей модели, напротив, используется значение по умолчанию, равное 10.  
  
```  
SELECT * INTO [New_Clustering]  
USING [Microsoft_Clustering] (CLUSTER_COUNT = 5)   
FROM [TM Clustering]  
```  
  
## <a name="example-2-adding-a-filter-to-the-model"></a>Пример 2: Добавление фильтра к модели  
 В следующем примере создается новая модель интеллектуального анализа данных на базе существующей модели интеллектуального анализа данных и к этой модели добавляется фильтр. Фильтр ограничивает обучающие данные тремя клиентами, которые проживают в определенном районе.  
  
```  
SELECT * INTO [Clustering Europe Region]  
USING [Microsoft_Clustering] WITH FILTER(Region='Europe')  
FROM [TM Clustering]  
```  
  
> [!NOTE]  
>  Фильтры, применяемые к таблице вариантов, можно изменить с помощью инструкции SELECT INTO, как показано в данном примере; однако, если исходная модель содержит фильтр для вложенной таблицы, этот фильтр нельзя изменить или удалить с помощью данной синтаксической конструкции; он будет копироваться из исходной модели в неизменном виде. Чтобы создать модели с другим фильтром для вложенной таблицы, используйте синтаксическую конструкцию ALTER STRTUCTURE...ADD MODEL.  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
