---
title: Алгоритмы интеллектуального анализа данных (SQL Server Data Mining Add-ins) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation
- data mining algorithms
- clustering [data mining]
- linear regression
- association [data mining]
- neural networks
- logistic regression
- regression
- sequence analysis
- decision tree [data mining]
- Naive Bayes
- time series [data mining]
ms.assetid: 3a1a62e4-9fb5-4cdb-a6c6-1b8b30d417ef
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b1feb34dca2fba1bad8829edff24ef1ce54e1fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161564"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a>Алгоритмы интеллектуального анализа данных (надстройки интеллектуального анализа данных SQL Server)
  Надстройки интеллектуального анализа данных для Office поддерживают создание аналитических моделей с использованием следующих алгоритмов интеллектуального анализа данных. Все алгоритмы основаны на широко известных методах машинного обучения и реализованы в Microsoft Research.  
  
## <a name="algorithms"></a>Алгоритмы  
  
|Метод машинного обучения|Принцип работы|  
|-----------------------------|------------------|  
|Алгоритм правил взаимосвязей Майкрософт|Узнайте, какие продукты приобретены совместно или какие события произошли одновременно, и воспользуйтесь моделью для создания рекомендаций.<br /><br /> [http://msdn.microsoft.com/library/ms174916.aspx](http://msdn.microsoft.com/library/ms174916.aspx)|  
|Алгоритм кластеризации (Майкрософт)|Определяйте сегменты рынка, автоматически группируйте взаимосвязанных заказчиков или находите связи в данных для использования в дальнейшем интеллектуальном анализе.<br /><br /> [http://msdn.microsoft.com/library/ms174879.aspx](http://msdn.microsoft.com/library/ms174879.aspx)|  
|Алгоритм дерева принятия решений (Майкрософт)|Определяйте ранее неизвестные связи между различными элементами пользовательских данных для лучшего информационного обоснования своих решений или находите факторы, которые приводят к конкретным результатам.<br /><br /> [http://msdn.microsoft.com/library/ms174923.aspx](http://msdn.microsoft.com/library/ms174923.aspx)|  
|Алгоритм линейной регрессии (Майкрософт)|Найдите математическую формулу, которая описывает факторы, влияющие на числовой результат.<br /><br /> [http://msdn.microsoft.com/library/ms174824.aspx](http://msdn.microsoft.com/library/ms174824.aspx)|  
|Алгоритм логистической регрессии (Майкрософт)|Идентифицируйте факторы, влияющие на двоичные результаты, и узнайте, как их использовать для воздействия на результаты.<br /><br /> [http://msdn.microsoft.com/library/ms174828.aspx](http://msdn.microsoft.com/library/ms174828.aspx)|  
|Упрощенный алгоритм Байеса (Майкрософт)|Исследуйте связи в данных и находите среди них те, которые имеют наиболее тесную корреляцию с результатом.<br /><br /> [http://msdn.microsoft.com/en-us/library/ms174806.aspx](http://msdn.microsoft.com/library/ms174806.aspx)|  
|Алгоритм нейронных сетей Майкрософт|Находите скрытые связи между несколькими входами и даже несколькими выходами. Используйте это для просмотра или для прогнозирования.<br /><br /> [http://msdn.microsoft.com/library/ms174941.aspx](http://msdn.microsoft.com/library/ms174941.aspx)|  
|Алгоритм временных рядов (Майкрософт)|Используйте исторические данные для прогнозирования будущих значений.<br /><br /> [http://msdn.microsoft.com/library/ms174923.aspx](http://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a>Дополнительные параметры  
 При использовании клиента интеллектуального анализа данных для Excel можно создавать собственные структуры и модели интеллектуального анализа данных или тонко настраивать параметры алгоритмов.  
  
 [Параметры алгоритма &#40;надстройки интеллектуального анализа данных SQL Server&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 Предусмотрены два способа настройки модели с использованием следующих дополнительных параметров:  
  
-   Используйте **запрос интеллектуального анализа данных** мастер для создания модели.  
  
-   В **клиента интеллектуального анализа данных**, то после запуска мастера, нажмите кнопку **параметры**.  
  
## <a name="see-also"></a>См. также  
 [Запрос &#40;надстройки интеллектуального анализа данных SQL Server&#41;](query-sql-server-data-mining-add-ins.md)   
 [Advanced моделирования &#40;интеллектуального анализа данных надстройки для Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  
