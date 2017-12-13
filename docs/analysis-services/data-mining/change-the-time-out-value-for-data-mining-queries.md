---
title: "Изменить значение времени ожидания для запросов интеллектуального анализа данных | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
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
ms.topic: article
helpviewer_keywords: time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d04cbc253fea4d12c142c4f755ffef2653fcd0b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a>изменить значение времени ожидания для запросов интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]При построении диаграммы точности прогнозов или выполнении прогнозирующего запроса, иногда может потребоваться много времени для создания всех данных, необходимых для формирования прогноза. Чтобы предотвратить возможность завершения запроса из-за истечения времени ожидания, можно изменить значение, управляющее тем, как долго сервер служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ожидает завершения запроса.  
  
 Значение по умолчанию равно 15, но этого может оказаться недостаточно, если модели являются сложными или источник данных имеет большой размер. При необходимости можно намного увеличить это значение, чтобы отвести достаточное количество времени для обработки. Например, если значение **Время ожидания запроса** равно 600, выполнение запроса может продолжаться до 10 минут.  
  
 Дополнительные сведения о прогнозирующих запросах см. в разделе [Задачи и инструкции по запросам интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md).  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a>Настройка значения времени ожидания для запросов интеллектуального анализа данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]в меню **Сервис** выберите пункт **Параметры**.  
  
2.  На панели **Параметры** разверните элемент **Конструкторы бизнес-аналитики**.  
  
3.  В текстовое поле **Время ожидания запроса** введите значение в секундах.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по запросам интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [Запросы интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
