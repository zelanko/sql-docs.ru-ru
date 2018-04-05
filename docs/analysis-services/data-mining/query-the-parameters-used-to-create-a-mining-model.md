---
title: Запросить параметры, используемые для создания модели интеллектуального анализа данных | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content queries [DMX]
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a35dc0d2279b73086af5c16d9d827a12221f63dd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a>запросить параметры, используемые для создания модели интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]На составление модели интеллектуального анализа данных влияют не только обучающие варианты, но и параметры, заданные при создании модели. Поэтому может быть полезно извлечь значения параметров существующей модели, чтобы лучше разобраться в ее поведении. Получение параметров также может быть полезным при создании документации по конкретной версии модели.  
  
 Для получения параметров, которые использовались при создании модели, нужно создать запрос к одному из наборов строк схемы модели интеллектуального анализа данных. Эти наборы строк схемы доступны как набор системных представлений, к которым легко осуществлять запросы с помощью синтаксиса Transact-SQL. В данной процедуре описывается создание запроса, возвращающего параметры, которые использовались для создания указанной модели интеллектуального анализа данных.  
  
### <a name="to-open-a-query-window-for-a-schema-rowset-query"></a>Открытие окна «Запрос» для запроса к набору строк схемы  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , содержащий модель, к которой создается запрос.  
  
2.  Щелкните правой кнопкой мыши имя экземпляра, выберите **Создать запрос**, а затем **Расширения интеллектуального анализа данных**.  
  
    > [!NOTE]  
    >  Можно также создать запрос к модели интеллектуального анализа данных с помощью шаблона **Многомерное выражение** .  
  
3.  Если в экземпляре содержится несколько баз данных, выберите в списке **Доступные базы данных** на панели инструментов базу данных, содержащую модель, к которой нужно создать запрос.  
  
### <a name="to-return-model-parameters-for-an-existing-mining-model"></a>Возврат параметров существующей модели интеллектуального анализа данных  
  
1.  На панели DMX-запросов введите или вставьте следующий текст.  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  Выберите в обозревателе объектов нужную модель интеллектуального анализа данных и перетащите ее на панель DMX-запросов, чтобы она оказалась заключенной в одиночные кавычки.  
  
3.  Нажмите клавишу F5 или кнопку **Выполнить**.  
  
## <a name="example"></a>Пример  
 Следующий программный код возвращает список параметров, которые использовались в учебнике [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)при создании модели интеллектуального анализа данных. В число этих параметров входят все значения по умолчанию, используемые службами интеллектуального анализа данных и предоставляемые поставщиками на сервере.  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 Данный пример кода возвращает для модели кластеризации следующие параметры.  
  
 Результаты eExample:  
  
 MINING_PARAMETERS  
  
 CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10  
  
## <a name="see-also"></a>См. также:  
 [Задачи и инструкции по запросам интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [Запросы интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
