---
title: "Обработка секций табличной модели (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c498d2b-22d6-4661-bc21-2ee708336c8b
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 188bd12ffbd91168f9960fa69ba696952c8b42c3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="process-tabular-model-partitions-ssas-tabular"></a>Обработка секций табличной модели (табличные службы SSAS)
  Секции разделяют таблицу на логические части. Каждая секция затем может обрабатываться (обновляться) независимо от других секций. Приведенные в этом разделе задачи описывают обработку секций в базе данных model с помощью диалогового окна **Обработка секций** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
###  <a name="bkmk_create_new"></a> Обработка секции  
  
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]щелкните правой кнопкой мыши таблицу, в которой есть секции для обработки, и выберите пункт **Секции**.  
  
2.  В диалоговом окне **Секции** на вкладке **Секции**нажмите кнопку «Обработка».  
  
3.  В диалоговом окне **Обработка секций** выберите один из следующих режимов из списка **Режим** :  
  
    |Режим|Description|  
    |----------|-----------------|  
    |**Обработка. По умолчанию**|Обнаруживает состояние обработки объекта секции и выполняет обработку, необходимую для перевода необработанных или частично обработанных объектов секции в полностью обработанное состояние. Выполняется загрузка данных для пустых таблиц и секций; иерархии, вычисляемые столбцы и связи строятся или перестраиваются.|  
    |**Обработка. Полная**|Обрабатывает объект секций и все объекты, которые в нем содержатся. Если объект, который обрабатывается методом полной обработки, уже был обработан, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляют все данные объекта, а затем обрабатывают его. Этот тип обработки требуется при внесении структурных изменений в объект.|  
    |**Обработка данных**|Выполняется загрузка данных в секцию или таблицу без перестроения иерархий или связей или повторного вычисления вычисленных столбцов и мер.|  
    |**Обработка с очисткой**|Удаляет все данные из секции.|  
    |**Обработка с добавлением**|Постепенно обновляет секцию с включением новых данных.|  
  
4.  В столбце флажков **Обработка** выберите секции для обработки в текущем режиме и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Секции табличных моделей (табличные службы SSAS)](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [Создание секций табличной модели и управление ими (табличные службы SSAS)](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
