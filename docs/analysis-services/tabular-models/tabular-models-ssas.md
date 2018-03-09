---
title: "Табличные модели | Документы Microsoft"
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 2df607b47e4bb2a5a770e27d1bceb5a6d7e6ebbc
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="tabular-models"></a>Табличные модели
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Табличные модели являются базами данных служб Analysis Services, выполняемыми в памяти или в режиме DirectQuery, которые обращаются к данным непосредственно из внутренних источников реляционных данных. Используя алгоритмов состояние современных сжатия и многопоточного обработчика запросов подсистема аналитики предоставляет быстрый доступ к объектам и данным табличной модели клиентских приложений, таких как Power BI и Excel.  
  
 Хотя моделей в памяти, проблема с автоматическим, DirectQuery — альтернативный режим запроса для моделей, которые слишком велики, чтобы поместиться в памяти, или изменчивость данных в которых препятствует выработке разумной стратегии обработки. DirectQuery позволяет достичь четности с моделями в памяти, благодаря поддержке широкого спектра источников данных, возможности обрабатывать вычисляемые таблицы и столбцы в модели DirectQuery, защите уровня строк посредством выражений DAX для доступа к серверной базе данных и запросов оптимизации, которые обеспечивают большую пропускную способность.
  
 Табличные модели создаются в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] с помощью шаблона проекта табличной модели, который предоставляет область конструктора для создания модели, таблиц, связей и выражений DAX. Можно импортировать данные из нескольких источников, а затем дополнить модель, добавив связи, вычисляемые таблицы и столбцы, меры, ключевые показатели эффективности и переводы.  
  
 Модели можно развернуть Azure Analysis Services или настроить экземпляр служб SQL Server Analysis Services в табличном режиме сервера. Можно управлять развертываемых табличных моделей в среде SQL Server Management Studio. По мере роста модели они могут секционировать для оптимизации обработки и защиту на уровне строк с помощью безопасности на основе ролей.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Решения табличных моделей](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md) -статьи в этом разделе описывают создание и развертывание решений табличной модели.
  
 [Базы данных табличной модели](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md) -статьи в этом разделе описывают управление решениями развернутой табличной модели.
  
 [Доступ к данным табличной модели](../../analysis-services/tabular-models/tabular-model-data-access.md) -статьи в этом разделе описаны подключение для развертывания решений табличных моделей.
  
## <a name="see-also"></a>См. также:  
 [Новые возможности служб Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Сравнение табличных и многомерных решений](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Средств и приложений, используемых в службах Analysis Services](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [Режим DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Уровень совместимости](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
