---
title: "Табличное моделирование (при уровне совместимости 1200) | Документы Microsoft"
ms.custom: 
ms.date: 01/17/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
keywords:
- "Службы Analysis Services"
- "Табличная модель"
- "Учебник"
- "Службы SSAS"
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 20248d68dc0371ef158f287d1f3a8bc9e87360d3
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="tabular-modeling-1200-compatibility-level"></a>Табличное моделирование (при уровне совместимости 1200)
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Этот учебник содержит уроки по созданию табличной модели служб Analysis Services в [уровне совместимости 1200](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md) с помощью [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)и развертывания модели служб Analysis Services сервер локально или в Azure.  
 
Если вы используете 2017 г. SQL Server или Azure Analysis Services и вы хотите создать модель на совместимость 1400 уровня, используйте [Azure Analysis Services — учебник по Adventure Works](https://review.docs.microsoft.com/azure/analysis-services/tutorials/aas-adventure-works-tutorial?branch=master). Эта обновленная версия использует новый, современный возможность получить данные для подключения и импорта исходных данных и использует язык M Настройка разделов.
 
  
## <a name="what-youll-learn"></a>Обзор учебника   
  
-   Инструкции по созданию нового проекта табличной модели в SSDT.
  
-   Импорт данных из реляционной базы данных SQL Server в проект табличной модели.  
  
-   Создание и управление связями между таблицами в модели.  
  
-   Создание и управление вычислениями, мерами и ключевыми показателями эффективности, которые помогут пользователям анализировать данные модели.  
  
-   Создание и управление перспективами и иерархиями, которые помогут пользователям просматривать данные модели, учитывая особенности предприятия и приложения.  
  
-   Создание секций, разделяющих табличные данные на более мелкие логические части, которые могут быть обработаны независимо от других секций.  
  
-   Обеспечение безопасности объектов моделей и данных за счет создания ролей и присвоения членства пользователям.  
  
-   Порядок развертывания табличной модели служб Analysis server в локальной или в Azure.  
  
## <a name="scenario"></a>Сценарий  
Этот учебник основывается на вымышленной компании Adventure Works Cycles. Adventure Works — это большая многонациональная производственная компания, производящая и реализующая металлические и Композитные велосипеды для рынков Северной Америки, Европы и Азии. С помощью headquarters в городе Ботель, штат Вашингтон компания ней работают 500 сотрудников. Кроме того Adventure Works использует несколько региональных групп продаж, на протяжении его рынков сбыта.  
  
Для обеспечения более качественной поддержки потребностей анализа данных отделов продаж и маркетинга и руководства необходимо создать табличную модель для пользователей с целью анализа данных интернет-продаж в образце базы данных AdventureWorksDW.  
  
Чтобы выполнить этот учебник и создать табличную модель Adventure Works по интернет-продажам, необходимо выполнить ряд занятий. В рамках каждого занятия есть ряд задач. Выполнение каждой задачи в нужном порядке является обязательным для завершения занятия. Когда в определенном занятии может быть несколько задач, которые приводят к схожему результату, но способ выполнения каждой задачи, немного отличается. Это показано, что часто более одного способа решения определенной задачи, а также чтобы стимулировать пользователя использовать навыки, вы узнали, при выполнении предыдущих задач.  
  
Цель занятий — провести пользователя через создание простой табличной модели, запущенной в режиме в памяти с использованием разных функций, включенных в SSDT. Поскольку каждое занятие строится на основе предыдущего занятия, их следует выполнять по порядку. После завершения всех занятий, будет создан и развернут образец Интернет-продаж Adventure Works табличной модели на сервере служб Analysis Services.  
  
Этот учебник не содержит занятий или сведений об управлении развернутой базой данных табличной модели с помощью среды SQL Server Management Studio или использовании клиентского приложения для создания отчетов для подключения к развернутой модели для просмотра данных модели.  
  
## <a name="prerequisites"></a>предварительные требования  
Чтобы завершить этот учебник, необходимо иметь следующие компоненты:  
  
-   Последняя версия [! ВКЛЮЧИТЬ[ssBIDevStudioFull](../ssdt/download-sql-server-data-tools-ssdt.md).

-   Последняя версия SQL Server Management Studio. [Получить последнюю версию](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 
  
-   Клиентское приложение, например [Power BI Desktop](https://powerbi.microsoft.com/desktop/) или [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel.    
  
-   Экземпляр SQL Server с образцом базы данных Adventure Works DW 2014. Этот образец базы данных включает данные, необходимые для выполнения заданий учебника. [Получить последнюю версию](http://go.microsoft.com/fwlink/?LinkID=335807).  
  

-   Azure Analysis Services или SQL Server 2016 или более поздней версии экземпляра служб Analysis Services для развертывания модели с целью. [Зарегистрируйтесь для получения бесплатной пробной версии Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/).
  
## <a name="lessons"></a>Занятия  
Этот учебник включает следующие занятия.  
  
|Занятие|Предположительное время выполнения|  
|----------|------------------------------|  
|[Занятие 1. Создание нового проекта табличной модели](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)|10 минут.|  
|[Занятие 2. Добавление данных](../analysis-services/lesson-2-add-data.md)|20 минут|  
|[Урок 3. Отметка в качестве таблицы дат](../analysis-services/lesson-3-mark-as-date-table.md)|3 минуты|  
|[Занятие 4: Создание связей](../analysis-services/lesson-4-create-relationships.md)|10 минут.|  
|[Занятие 5: Создание вычисляемых столбцов](../analysis-services/lesson-5-create-calculated-columns.md)|15 минут|
|[Занятие 6: Создание мер](../analysis-services/lesson-6-create-measures.md)|30 минут|  
|[Урок 7. Создание ключевых показателей эффективности](../analysis-services/lesson-7-create-key-performance-indicators.md)|15 минут|  
|[Занятие 8: Создание перспектив](../analysis-services/lesson-8-create-perspectives.md)|5 минут|  
|[Занятие 9: Создание иерархий](../analysis-services/lesson-9-create-hierarchies.md)|20 минут|  
|[Занятие 10: Создание секций](../analysis-services/lesson-10-create-partitions.md)|15 минут|  
|[Занятие 11: Создание ролей](../analysis-services/lesson-11-create-roles.md)|15 минут|  
|[Урок 12. Анализ в Excel](../analysis-services/lesson-12-analyze-in-excel.md)|20 минут| 
|[Урок 13. Развертывание](../analysis-services/lesson-13-deploy.md)|5 минут|  
  
## <a name="supplemental-lessons"></a>Дополнительные занятия  
Этот учебник также включает в себя [дополнительные занятия](http://msdn.microsoft.com/library/2018456f-b4a6-496c-89fb-043c62d8b82e). Ознакомление с содержащимися здесь разделами не требуется для прохождения этого учебника, но может оказаться полезным для лучшего освоения функций для работы с расширенной табличной моделью.  
  
|Занятие|Предположительное время выполнения|  
|----------|------------------------------|  
|[Реализация динамической безопасности с помощью фильтров строк](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)|30 минут|  

  
## <a name="next-step"></a>Следующий шаг  
Чтобы приступить к изучению этого учебника, перейдите к первому занятию: [Занятие 1. Создание нового проекта табличной модели](../analysis-services/lesson-1-create-a-new-tabular-model-project.md).  
  
  
  

