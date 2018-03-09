---
title: "Производительность, моментальные снимки, кэширование (службы Reporting Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: 85afd00f-e8d7-4ef7-9174-2ff84d82f960
caps.latest.revision: "20"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 90444a549b665fb1577b829df3ddae46687565fa
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="performance-snapshots-caching-reporting-services"></a>Производительность, моментальные снимки, кэширование (службы Reporting Services)
  Производительность сервера отчетов зависит от сочетания факторов, которые включают оборудование, количество пользователей, одновременно обращающихся к отчетам, объем данных в отчетах и формат вывода. Чтобы понять, какие факторы производительности характерны для конкретной установки, и какие меры позволят достичь требуемых результатов, необходимо получить базовые данные и выполнить тесты. Дополнительные сведения о средствах и рекомендациях см. в следующих публикациях MSDN: [Reporting Services Performance Optimization](http://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) (Оптимизация производительности служб Reporting Services) и [Using Visual Studio 2005 to Perform Load Testing on a SQL Server 2005 Reporting Services Report Server](http://go.microsoft.com/fwlink/?LinkID=77519)(Нагрузочное тестирование сервера отчетов служб Reporting Services SQL Server 2005 в среде Visual Studio 2005).  
  
 Общие принципы, которыми необходимо руководствоваться, включают следующее.  
  
-   Операции обработки и подготовки к просмотру отчетов требуют много памяти. По возможности выбирайте компьютер со значительным объемом памяти.  
  
-   Размещение сервера отчетов и базы данных сервера отчетов на отдельных компьютерах, как правило, позволяет достичь более высокой производительности по сравнению с тем вариантом, когда они размещаются на одном компьютере, пусть даже высокого класса.  
  
-   Если все отчеты обрабатываются медленно, рассмотрите возможность масштабного развертывания, в котором несколько экземпляров сервера отчетов поддерживают единственную базу данных сервера отчетов. Для достижения наилучших результатов используйте подсистему балансировки загрузки, чтобы равномерно распределить запросы по всему развертыванию.  
  
-   Если единственный отчет обрабатывается медленно, то необходимо настроить запросы набора данных отчета, если этот отчет должен выполняться по запросу. Можно также рассмотреть возможность использования общих наборов данных, которые можно кэшировать, кэшируя отчет или запуская отчет в качестве моментального снимка.  
  
-   Если медленно обрабатываются все отчеты в конкретном формате (например, на этапе подготовки к просмотру в формате PDF), рассмотрите возможность доставки в общую папку, добавления большего объема памяти или выбора другого формата.  
  
-   Чтобы узнать, сколько времени занимает обработка отчета, и ознакомиться с другими показателями производительности, просмотрите журнал выполнения сервера отчетов. Дополнительные сведения см. в разделе [Журнал выполнения сервера отчетов и представление ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
-   Дополнительные сведения о снижении остроты проблем производительности путем настройки конфигурации управления памятью см. в разделе [Настройка доступной памяти для приложений сервера отчетов](../../reporting-services/report-server/configure-available-memory-for-report-server-applications.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Наблюдение за производительностью сервера отчетов](../../reporting-services/report-server/monitoring-report-server-performance.md)  
 Описывает объекты производительности, которые можно использовать для слежения за рабочей нагрузкой сервера.  
  
 [Установка свойств обработки отчетов](../../reporting-services/report-server/set-report-processing-properties.md)  
 Описывает способы настройки отчета для запуска по запросу, из кэша или по расписанию в качестве моментального снимка отчета.  
  
 [Настройка доступной памяти для приложений сервера отчетов](../../reporting-services/report-server/configure-available-memory-for-report-server-applications.md)  
 Рассматривается переопределение поведения управления памятью по умолчанию.  
  
 [Кэширование отчетов (службы SSRS)](../../reporting-services/report-server/caching-reports-ssrs.md)  
 Описывает поведение кэширования отчета на сервере отчетов.  
  
 [Общие наборы данных в кэше (службы SSRS)](../../reporting-services/report-server/cache-shared-datasets-ssrs.md)  
 Описывает работу кэширования общего набора данных на сервере отчетов.  
  
 [Обработка больших отчетов](../../reporting-services/report-server/process-large-reports.md)  
 Содержит рекомендации о настройке и распределении большого отчета.  
  
 [Задание значений времени ожидания при обработке отчетов и общих наборов данных (SSRS)](../../reporting-services/report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
 Объясняет, как устанавливаются истечения времени ожидания при обработке запросов и отчетов.  
  
## <a name="see-also"></a>См. также:  
 [Управление запущенным процессом](../../reporting-services/subscriptions/manage-a-running-process.md)   
 [Проверка запуска отчета](../../reporting-services/report-server/verifying-a-report-run.md)  
  
  
