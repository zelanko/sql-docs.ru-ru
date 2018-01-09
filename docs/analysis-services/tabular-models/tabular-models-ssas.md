---
title: "Табличные модели (службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2017
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
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 8c7b3af6a309be12a58ae666de50ad702fe1fbd1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="tabular-modeling-ssas"></a>Табличное моделирование (службы SSAS)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Табличные модели являются базами данных служб Analysis Services, выполняемые в памяти или в режиме DirectQuery, доступ к данным непосредственно из внутренних источников реляционных данных.  
  
 По умолчанию используется выполнение в памяти. С помощью современных алгоритмов сжатия и многопоточного обработчика запросов подсистема выполняющейся в памяти аналитики предоставляет быстрый доступ к объектам табличной модели и данным через клиентские приложения создания отчетов, такие как Microsoft Excel и Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
 DirectQuery — это альтернативный режим запроса для моделей, которые слишком велики, чтобы поместиться в памяти, или изменчивость данных в которых препятствует выработке разумной стратегии обработки. В этом выпуске режим DirectQuery вышел на один уровень с моделями, выполняемыми в памяти, благодаря поддержке дополнительных источников данных, возможности обрабатывать вычисляемые таблицы и столбцы в модели DirectQuery, защите уровня строк посредством выражений DAX, охватывающих серверную базу данных, а также оптимизациям запросов, которые обеспечивают большую пропускную способность, чем предыдущие версии.
  
 Табличные модели создаются в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] с помощью шаблона проекта табличной модели, который предоставляет область конструктора для создания модели, таблиц, связей и выражений DAX. Можно импортировать данные из нескольких источников, а затем дополнить модель, добавив связи, вычисляемые таблицы и столбцы, меры, ключевые показатели эффективности и переводы.  
  
 Затем модели можно развернуть в экземпляре служб Analysis Services, настроенном для табличного режима, где клиентские приложения создания отчетов могут подключаться к ним. Развернутыми моделями можно управлять в среде SQL Server Management Studio как многомерными моделями. Также они могут быть секционированы для оптимизации обработки и защиты на уровне строк с помощью безопасности на основе ролей.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Решения табличных моделей (табличные службы SSAS)](../../analysis-services/tabular-models/tabular-model-solutions-ssas-tabular.md): в подразделах этого раздела описывается создание и развертывание решений табличных моделей.
  
 [Базы данных табличных моделей (табличные службы SSAS)](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md): в подразделах этого раздела описывается управление развернутыми решениями табличных моделей.
  
 [Доступ к данным табличной модели](../../analysis-services/tabular-models/tabular-model-data-access.md): в подразделах этого раздела описывается подключение к развернутым решениям табличных моделей.
  
## <a name="see-also"></a>См. также:  
 [Новые возможности в службах Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Сравнение табличных и многомерных решений (службы SSAS)](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Средств и приложений, используемых в службах Analysis Services](../../analysis-services/tools-and-applications-used-in-analysis-services.md)   
 [Режим DirectQuery (табличные службы SSAS)](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
