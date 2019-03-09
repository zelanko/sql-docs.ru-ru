---
title: Учебник по службам Analysis Services Adventure Works (1400) | Документация Майкрософт
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d4fae7f55543be52342692d344f250f8e08ba877
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685491"
---
# <a name="tabular-modeling-1400-compatibility-level"></a>Табличное моделирование (с уровнем совместимости 1400)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

О том, как создание и развертывание табличной модели в в этом учебнике содержатся занятия [уровнем совместимости 1400](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md). Если вы не знакомы со служб Analysis Services и табличным моделированием, изучения этого учебника — это самый быстрый способ научиться создавать и развертывать простые табличные модели с помощью Visual Studio. При наличии необходимых компонентов на месте, займет 2 – 3 часов.  
  
## <a name="what-you-learn"></a>Вы узнаете   
  
-   Создание нового проекта табличной модели в **уровнем совместимости 1400** на SSDT в Visual Studio.
  
-   Как импортировать данные из реляционной базы данных в базу данных рабочей области проекта табличной модели.  
  
-   Создание и управление связями между таблицами в модели.  
  
-   Как создать вычисляемые столбцы, меры и ключевые показатели эффективности, которые помогут пользователям анализировать критические бизнес-метрики.  
  
-   Как создать и управление перспективами и иерархиями, которые помогут пользователям просматривать данные модели, предоставляя бизнеса и точки зрения конкретного приложения.  
  
-   Создание секций, разделяющих табличные данные на более мелкие логические части, которые могут быть обработаны независимо от других секций.  
  
-   Обеспечение безопасности объектов моделей и данных за счет создания ролей и присвоения членства пользователям.  
  
-   Развертывание табличной модели, чтобы **Azure Analysis Services** сервера или **SQL Server 2017 Analysis Services** сервера с помощью SSDT.  
  
## <a name="prerequisites"></a>предварительные требования  

Для работы с этим руководством вам потребуется:  
  
-   Сервер Azure Analysis Services или сервером SQL Server 2017 Analysis Services в табличном режиме. Зарегистрируйтесь для получения бесплатной [пробной версии служб Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/) и [создание сервера](https://docs.microsoft.com/azure/analysis-services/analysis-services-create-server) или загрузить бесплатные [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).

-   [Хранилище данных SQL Azure](https://docs.microsoft.com/azure/sql-data-warehouse/create-data-warehouse-portal) с **образца базы данных AdventureWorksDW**, или хранилище данных на локальном SQL Server с [образец базы данных AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). При установке хранилища данных SQL Server в локальной базе данных AdventureWorksDW, используйте версию образец БД, соответствующую в вашей версии сервера. 

    **Внимание!** Если установить образец базы данных в хранилище данных SQL Server в локальной и развернуть модель на сервере служб Azure Analysis Services, [локальный шлюз данных](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) является обязательным.

-   Последнюю версию [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx). Или, если у вас уже есть Visual Studio 2017, можно загрузить и установить [проекты служб Microsoft Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) пакета (VSIX). В этом руководстве описано ссылки на SSDT и Visual Studio являются синонимами. 

-   Последнюю версию [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).    

-   Клиентское приложение, например [Power BI Desktop](https://powerbi.microsoft.com/desktop/) или Excel. 

## <a name="scenario"></a>Сценарий  

Этот учебник основан на вымышленной компании Adventure Works Cycles. Adventure Works — это большой производственная компания, выпускающая и реализующая велосипеды, запчасти и аксессуары для рынков Северной Америки, Европы и Азии. Штат компании насчитывает 500 сотрудников. Кроме того Adventure Works использует несколько региональных групп продаж, ее рынкам сбыта. Проект — Создать табличную модель для продаж и маркетинга пользователям анализировать данные Интернет-продаж в базе данных AdventureWorksDW.  
  
Для работы с учебником, вы несколько занятий. На каждом занятии есть задачи. Завершение работы каждой задачи в порядке необходимо решить. Хотя в определенном занятии может быть несколько задач, которые приводят к схожему результату, но способ выполнения каждой задачи немного отличается. Этот метод показывает, что часто есть несколько способов для выполнения задачи и стимулирует вас применять полученные знания на предыдущих занятиях и задачи.  
  
Цель занятий — провести пользователя через создание простой табличной модели с использованием разных функций, доступных в SSDT. Поскольку каждое занятие строится на основе предыдущего занятия, их следует выполнять по порядку.
  
Этот учебник не обучает управлению сервером на портале Azure, управлению сервера или базы данных с помощью SSMS или с помощью клиентского приложения для просмотра данных модели. 


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

Эти занятия не требуются для работы с учебником, но могут оказаться полезными при более общие сведения о расширенной табличной модели компонентов.  
  
|Занятие|Предположительное время выполнения|  
|----------|------------------------------|  
|[Строки детализации](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)|10 минут.|
|[Динамическая безопасность](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)|30 минут|
|[Неоднородные иерархии](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)|20 минут| 

  
## <a name="next-steps"></a>Следующие шаги  

Чтобы приступить к работе, см. в разделе [занятии 1: Создание нового проекта табличной модели](../tutorial-tabular-1400/as-lesson-1-create-a-new-tabular-model-project.md).  
  
  
  

