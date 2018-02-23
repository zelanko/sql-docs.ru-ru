---
title: "Учебник по службам Analysis Services Adventure Works (1400) | Документы Microsoft"
description: "Предоставляет учебник по Adventure Works для служб Analysis Services"
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: 8a7511c096ffacf249187c9f45d71bca340bb1ca
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="tabular-modeling-1400-compatibility-level"></a>Табличное моделирование (уровень совместимости 1400)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Этот учебник состоит из уроков, о том, как создать и развернуть табличную модель на [уровень совместимости 1400](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md). Если вы не знакомы с Analysis Services и табличного моделирования, изучения этого учебника является самым быстрым способом узнать, как создание и развертывание табличной модели с помощью Visual Studio. При наличии необходимых компонентов на месте займет двух до трех часов.  
  
## <a name="what-you-learn"></a>Полученные знания   
  
-   Создание нового проекта табличной модели в **уровень совместимости 1400** в Visual Studio с помощью SSDT.
  
-   Как импортировать данные из реляционной базы данных в базу данных рабочей области проекта табличной модели.  
  
-   Создание и управление связями между таблицами в модели.  
  
-   Как создать вычисляемые столбцы, меры и ключевые индикаторы производительности, которые помогут пользователям анализировать метрики критически важные для бизнеса.  
  
-   Способы создания и управление перспективами и иерархиями, которые помогут пользователям просматривать данные модели, предоставляя бизнеса и точки зрения конкретного приложения.  
  
-   Создание секций, разделяющих табличные данные на более мелкие логические части, которые могут быть обработаны независимо от других секций.  
  
-   Обеспечение безопасности объектов моделей и данных за счет создания ролей и присвоения членства пользователям.  
  
-   Развертывание табличной модели, чтобы **Azure Analysis Services** сервера или **служб аналитики SQL Server 2017 г** сервера с помощью SSDT.  
  
## <a name="prerequisites"></a>предварительные требования  

Для работы с этим учебником необходимо:  
  
-   Сервер служб Azure Analysis Services или SQL Server 2017 г. сервер Analysis Services в табличном режиме. Подпишитесь на бесплатную [пробной версии Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/) и [создать сервер](https://docs.microsoft.com/azure/analysis-services/analysis-services-create-server) или загрузить бесплатные [SQL Server 2017 г Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).

-   [Хранилище данных SQL Azure](https://docs.microsoft.com/azure/sql-data-warehouse/create-data-warehouse-portal) с **образец базы данных AdventureWorksDW**, или хранилище данных локального SQL Server с [образца базы данных AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). При установке базы данных AdventureWorksDW для хранилища данных SQL Server в локальной среде, используйте версию образца БД, которая соответствует с версией сервера. 

    **Важно:** при установке образца базы данных к хранилищу данных SQL Server в локальной среде и развертывания модели на сервере служб Azure Analysis Services, [локального шлюза данных](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) является обязательным.

-   Последнюю версию [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx). Или, при наличии Visual Studio 2017 г. можно загрузить и установить [проекты служб Microsoft Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) пакета (VSIX). В этом учебнике ссылки на Visual Studio и SSDT являются синонимами. 

-   Последнюю версию [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).    

-   Клиентское приложение, например [Power BI Desktop](https://powerbi.microsoft.com/desktop/) или Excel. 

## <a name="scenario"></a>Сценарий  

Этот учебник основывается на вымышленной компании Adventure Works Cycles. Adventure Works — это большой, многонациональная производственная компания, производящая и реализующая велосипедов, элементы и стандартные для рынков Северной Америки, Европы и Азии. Компания использует 500 сотрудников. Кроме того Adventure Works использует несколько региональных групп продаж, на протяжении его рынков сбыта. Проект состоит в создании табличной модели для продаж и маркетинга пользователей для анализа данных Интернет-продаж в базы данных AdventureWorksDW.  
  
Для прохождения этого учебника, необходимо выполнить различные занятий. На каждом занятии есть задачи. Выполнение каждой задачи в порядке, необходимые для завершения занятия. Когда в определенном занятии может быть несколько задач, которые приводят к схожему результату, но способ выполнения каждой задачи, немного отличается. Этот метод показывает, что составляет часто более чем одним способом для выполнения задачи и чтобы стимулировать пользователя использовать навыки, вы узнали в предыдущих уроках и задачах.  
  
Цель занятий — провести пользователя через создание простой табличной модели с использованием разных функций, включенных в SSDT. Поскольку каждое занятие строится на основе предыдущего занятия, их следует выполнять по порядку.
  
Этот учебник не содержит занятий по управлению сервером на портале Azure, управление с помощью SSMS или с помощью клиентского приложения для просмотра данных модели сервера или базы данных. 


## <a name="lessons"></a>Занятия  

Этот учебник включает следующие занятия.  
  
|Занятие|Предположительное время выполнения|  
|----------|------------------------------|  
|[1 - Создание нового проекта табличной модели](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md)|10 минут.|  
|[2. Получение данных](../tutorial-tabular-1400/as-lesson-2-get-data.md)|10 минут.|  
|[3. Отметка в качестве таблицы дат](../tutorial-tabular-1400/as-lesson-3-mark-as-date-table.md)|3 минуты|  
|[4. Создание связей](../tutorial-tabular-1400/as-lesson-4-create-relationships.md)|10 минут.|  
|[5. Создание вычисляемых столбцов](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md)|15 минут|
|[6. Создание мер](../tutorial-tabular-1400/as-lesson-6-create-measures.md)|30 минут|  
|[7 - создание ключевых показателей эффективности (KPI)](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)|15 минут|  
|[8. Создание перспектив](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md)|5 минут|  
|[9. Создание иерархий](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)|20 минут|  
|[10. Создание секций](../tutorial-tabular-1400/as-lesson-10-create-partitions.md)|15 минут|  
|[11. Создание ролей](../tutorial-tabular-1400/as-lesson-11-create-roles.md)|15 минут|  
|[12. Анализ в Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)|5 минут| 
|[13. Развертывание](../tutorial-tabular-1400/as-lesson-13-deploy.md)|5 минут|  
  
## <a name="supplemental-lessons"></a>Дополнительные занятия  

Эти занятия не являются обязательными для прохождения этого учебника, но могут быть полезны для улучшения понимания расширенной табличной моделью функции.  
  
|Занятие|Предположительное время выполнения|  
|----------|------------------------------|  
|[Строки детализации](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)|10 минут.|
|[Динамическая безопасность](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)|30 минут|
|[Неоднородные иерархии](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)|20 минут| 

  
## <a name="next-steps"></a>Следующие шаги  

Чтобы приступить к работе, см. [занятия 1: Создание нового проекта табличной модели](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
  
  

