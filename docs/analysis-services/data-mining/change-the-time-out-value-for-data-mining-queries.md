---
title: Изменить значение времени ожидания для запросов интеллектуального анализа данных | Документация Майкрософт
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c67744ea3862185b59d1a0af3e1bb144eba57e23
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62671009"
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a>изменить значение времени ожидания для запросов интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  При построении диаграммы точности прогнозов или выполнении прогнозирующего запроса иногда может потребоваться много времени для создания всех данных, необходимых для формирования прогноза. Чтобы предотвратить возможность завершения запроса из-за истечения времени ожидания, можно изменить значение, управляющее тем, как долго сервер служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ожидает завершения запроса.  
  
 Значение по умолчанию равно 15, но этого может оказаться недостаточно, если модели являются сложными или источник данных имеет большой размер. При необходимости можно намного увеличить это значение, чтобы отвести достаточное количество времени для обработки. Например, если значение **Время ожидания запроса** равно 600, выполнение запроса может продолжаться до 10 минут.  
  
 Дополнительные сведения о прогнозирующих запросах см. в разделе [Задачи и инструкции по запросам интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md).  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a>Настройка значения времени ожидания для запросов интеллектуального анализа данных  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]в меню **Сервис** выберите пункт **Параметры**.  
  
2.  На панели **Параметры** разверните элемент **Конструкторы бизнес-аналитики**.  
  
3.  В текстовое поле **Время ожидания запроса** введите значение в секундах.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по запросам интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [Запросы интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
