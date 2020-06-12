---
title: Алгоритмы интеллектуального анализа данных (SQL Server надстройки интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 3a73ce5a538756a740afd2db72d585fa54f03cae
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84525933"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a>Алгоритмы интеллектуального анализа данных (надстройки интеллектуального анализа данных SQL Server)
  Надстройки интеллектуального анализа данных для Office поддерживают создание аналитических моделей с использованием следующих алгоритмов интеллектуального анализа данных. Все алгоритмы основаны на широко известных методах машинного обучения и реализованы в Microsoft Research.  
  
## <a name="algorithms"></a>Алгоритмы  
  
|Метод машинного обучения|Принцип работы|  
|-----------------------------|------------------|  
|Алгоритм правил взаимосвязей Майкрософт|Узнайте, какие продукты приобретены совместно или какие события произошли одновременно, и воспользуйтесь моделью для создания рекомендаций.<br /><br /> [https://msdn.microsoft.com/library/ms174916.aspx](https://msdn.microsoft.com/library/ms174916.aspx)|  
|Алгоритм кластеризации (Майкрософт)|Определяйте сегменты рынка, автоматически группируйте взаимосвязанных заказчиков или находите связи в данных для использования в дальнейшем интеллектуальном анализе.<br /><br /> [https://msdn.microsoft.com/library/ms174879.aspx](https://msdn.microsoft.com/library/ms174879.aspx)|  
|Алгоритм дерева принятия решений (Майкрософт)|Определяйте ранее неизвестные связи между различными элементами пользовательских данных для лучшего информационного обоснования своих решений или находите факторы, которые приводят к конкретным результатам.<br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
|Алгоритм линейной регрессии (Майкрософт)|Найдите математическую формулу, которая описывает факторы, влияющие на числовой результат.<br /><br /> [https://msdn.microsoft.com/library/ms174824.aspx](https://msdn.microsoft.com/library/ms174824.aspx)|  
|Алгоритм логистической регрессии (Майкрософт)|Идентифицируйте факторы, влияющие на двоичные результаты, и узнайте, как их использовать для воздействия на результаты.<br /><br /> [https://msdn.microsoft.com/library/ms174828.aspx](https://msdn.microsoft.com/library/ms174828.aspx)|  
|Упрощенный алгоритм Байеса (Майкрософт)|Исследуйте связи в данных и находите среди них те, которые имеют наиболее тесную корреляцию с результатом.<br /><br /> [https://msdn.microsoft.com/library/ms174806.aspx](https://msdn.microsoft.com/library/ms174806.aspx)|  
|Алгоритм нейронных сетей Майкрософт|Находите скрытые связи между несколькими входами и даже несколькими выходами. Используйте это для просмотра или для прогнозирования.<br /><br /> [https://msdn.microsoft.com/library/ms174941.aspx](https://msdn.microsoft.com/library/ms174941.aspx)|  
|Алгоритм временных рядов (Майкрософт)|Используйте исторические данные для прогнозирования будущих значений.<br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a>Дополнительные параметры  
 При использовании клиента интеллектуального анализа данных для Excel можно создавать собственные структуры и модели интеллектуального анализа данных или тонко настраивать параметры алгоритмов.  
  
 [Параметры алгоритма &#40;SQL Server надстройки интеллектуального анализа данных&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 Предусмотрены два способа настройки модели с использованием следующих дополнительных параметров:  
  
-   Используйте мастер **запросов интеллектуального анализа данных** для создания модели.  
  
-   В **клиенте интеллектуального анализа данных**после запуска мастера нажмите кнопку **Параметры**.  
  
## <a name="see-also"></a>См. также:  
 [&#40;запросов SQL Server надстройки интеллектуального анализа данных&#41;](query-sql-server-data-mining-add-ins.md)   
 [Расширенное моделирование &#40;надстройки интеллектуального анализа данных для Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  
