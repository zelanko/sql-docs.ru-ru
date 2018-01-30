---
title: "Табличные модели | Документы Microsoft"
ms.custom: 
ms.date: 01/29/2018
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
ms.openlocfilehash: edeea89c1d767364f4f087d0f4b2e6d566895c52
ms.sourcegitcommit: c77a8ac1ab372927c09bf241d486e96881b61ac9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
# <a name="tabular-models"></a>Табличные модели
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Табличные модели являются базами данных служб Analysis Services, выполняемые в памяти или в режиме DirectQuery, доступ к данным непосредственно из внутренних источников реляционных данных.  
  
 По умолчанию используется выполнение в памяти. С помощью алгоритмов состояние современных сжатия и многопоточного обработчика запросов, подсистема аналитики предоставляет быстрый доступ к объектам и данным табличной модели клиентских приложений, таких как Power BI и Excel.  
  
 DirectQuery — это альтернативный режим запроса для моделей, которые слишком велики, чтобы поместиться в памяти, или изменчивость данных в которых препятствует выработке разумной стратегии обработки. В этом выпуске режим DirectQuery вышел на один уровень с моделями, выполняемыми в памяти, благодаря поддержке дополнительных источников данных, возможности обрабатывать вычисляемые таблицы и столбцы в модели DirectQuery, защите уровня строк посредством выражений DAX, охватывающих серверную базу данных, а также оптимизациям запросов, которые обеспечивают большую пропускную способность, чем предыдущие версии.
  
 Табличные модели создаются в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] с помощью шаблона проекта табличной модели, который предоставляет область конструктора для создания модели, таблиц, связей и выражений DAX. Можно импортировать данные из нескольких источников, а затем дополнить модель, добавив связи, вычисляемые таблицы и столбцы, меры, ключевые показатели эффективности и переводы.  
  
 Модели можно развернуть Azure Analysis Services или настроить экземпляр служб SQL Server Analysis Services в табличном режиме сервера. Можно управлять развертываемых табличных моделей в среде SQL Server Management Studio как многомерными моделями. Также они могут быть секционированы для оптимизации обработки и защиты на уровне строк с помощью безопасности на основе ролей.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Решения табличных моделей](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md) -в этом разделе описывают создание и развертывание решений табличной модели.
  
 [Базы данных табличной модели](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md) -в этом разделе описывают управление решениями развернутой табличной модели.
  
 [Доступ к данным табличной модели](../../analysis-services/tabular-models/tabular-model-data-access.md) -подразделы данного раздела описывают подключение для развертывания решений табличных моделей.
  
## <a name="see-also"></a>См. также:  
 [Новые возможности в службах Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Сравнение табличных и многомерных решений](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Средств и приложений, используемых в службах Analysis Services](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [Режим DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
