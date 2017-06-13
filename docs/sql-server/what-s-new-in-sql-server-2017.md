---
title: "Какой &#39; новые возможности SQL Server 2017 г. | Документы Microsoft"
ms.custom: 
ms.date: 05/23/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 1d363db8e8bd0e1460cdea3c3a7add68e48714c9
ms.openlocfilehash: 25d81efe1b915f0e4ddc5eab2feb4142ad2ceb8f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/05/2017

---
# <a name="what39s-new-in-sql-server-2017"></a>Какой &#39; новые возможности SQL Server 2017 г.
2017 г. SQL Server представляет важный шаг к созданию сервера SQL платформу, которая позволяет выбрать либо языков разработки, типы данных, в локальной среде и в облаке, так и в операционных системах путем приведения возможности SQL Server в контейнеры Docker на основе Linux, Windows и Linux.

В этом разделе приведена сводка новые возможности в самой последней версии Technical Preview сообщества (CTP) и ссылки на дополнительные возможности новых сведений о конкретных функциональных областях.

![info_tip](../sql-server/media/info-tip.png) Запуск SQL Server в Linux Дополнительные сведения см. в разделе:
-  [Новые возможности для 2017 г. SQL Server в Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-whats-new)
-  [Документация по SQL Server на платформе Linux](https://docs.microsoft.com/sql/linux/)


**Попробуйте продукт:**    
   -   [![Загрузить из центра оценки](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  **[загрузить SQL Server 2017 г Community Technology Preview](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="whats-new-in-sql-server-2017-ctp-21-may-2017"></a>Новые возможности SQL Server 2017 г CTP 2.1 (май 2017 г.)
### <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine  
- Новый DMF [sys.dm_db_log_stats](../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md), введенные для предоставления сводных уровня атрибуты и сведения о файлах журнала транзакций; полезны для мониторинга работоспособности журнала транзакций.  
- Эта CTP-версия содержит исправления и улучшения производительности для компонента Database Engine.
- Подробный список 2017 г. усовершенствования CTP-версии в предыдущих выпусках CTP-версии, в разделе [новые возможности SQL Server 2017 г. (компонент Database Engine)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

### <a name="sql-server-reporting-services-ssrs"></a>Службы SQL Server Reporting Services (SSRS)
- SQL Server Reporting Services больше не доступно для установки программой установки SQL Server, начиная с CTP-версии 2.1.
- Комментарии, теперь доступны для отчетов. Комментарии позволяют добавить перспективу для возможности отчета и совместной работы с другими пользователями в вашей организации. Можно также включить вложения в комментарий.
- Более подробные сведения о новых возможностях SSRS, включая сведения из предыдущих выпусков, см. в статье [Новые возможности служб Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 
- Сведения о сервере отчетов Power BI см. в разделе [приступить к работе с сервером отчетов Power BI](https://powerbi.microsoft.com/documentation/reportserver-get-started/).

### <a name="sql-server-machine-learning-services"></a>Изучение служб машины SQL Server
- Нет новых компонентов службы обучения машины в этой CTP-версии.
- Более подробные службы обучения машины новой информации, включая данные из предыдущей CTP-версии, видят [новые возможности служб SQL Server Machine Learning](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).  

### <a name="sql-server-analysis-services-ssas"></a>Службы SQL Server Analysis Services (SSAS)
- В этой CTP-версии нет новых функций SSAS.  
- Дополнительные сведения об улучшениях и исправления ошибок в этом выпуске см. в разделе [новые возможности служб Analysis Services SQL Server 2017 г](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  

### <a name="sql-server-integration-services-ssis"></a>Службы SQL Server Integration Services
-   Теперь вы можете использовать **Use32BitRuntime** параметра.
-   Улучшена производительность ведения журнала.
- Более подробные служб SSIS новые сведения, включая сведения из предыдущей CTP-версии, видят [новые возможности служб интеграции SQL Server 2017 г](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).  

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="whats-new-in-sql-server-2017-ctp-20-april-2017"></a>Новые возможности SQL Server 2017 г CTP 2.0 (апрель 2017 г.)
### <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine
- **Перестроение индекса в сети возобновляемые**. Перестроение индекса в сети возобновляемые позволяет возобновить операции перестроения индекса в сети с места остановки после сбоя. Например отработка отказа для реплики или ситуации недостаточно дискового пространства. Можно также приостанавливать и возобновлять операции перестроения индекса в сети. Например может потребоваться временно освободить ресурсы системы с целью выполнения задача с высоким приоритетом или выполнить перестроение индекса в другом окне miniatous обслуживания windows в случае слишком мало для большой таблицы. И, наконец перестроение индекса в сети возобновляемые значительную нагрузку на журнал пространства, что позволяет выполнять усечение журнала во время выполнения операции перестроения возобновляемые не требуется. В разделе [ALTER INDEX](../t-sql/statements/alter-index-transact-sql.md) и [руководящие принципы для операций с индексами в сети](../relational-databases/indexes/guidelines-for-online-index-operations.md).
- **Параметр IDENTITY_CACHE для инструкции ALTER DATABASE SCOPED CONFIGURATION**. Был добавлен новый параметр IDENTITY_CACHE инструкция ALTER DATABASE области конфигурации T-SQL. Если этот параметр имеет значение OFF, пропуски можно избежать в качестве значений столбцов идентификаторов в случае сервер неожиданно перезапускается или при сбое сервера-получателя. В разделе [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).  
- Среда CLR использует CAS (Разграничение доступа кода) в .NET Framework, которая больше не поддерживается в качестве границы безопасности. Сборки среды CLR, созданные с `PERMISSION_SET = SAFE` можно получить доступ к внешним системным ресурсам, вызов неуправляемого кода и получения прав системного администратора. Начиная с версии [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)], `sp_configure` возможность, называемую `clr strict security` впервые появился в целях повышения безопасности сборок среды CLR. `clr strict security`включено по умолчанию и рассматривает `SAFE` и `EXTERNAL_ACCESS` сборки как если бы они были помечены `UNSAFE`. `clr strict security` Параметр можно отключить для обеспечения обратной совместимости, но не рекомендуется. Корпорация Майкрософт рекомендует всем сборкам быть подписан сертификата или ассиметричного ключа, соответствующего имени входа, которому предоставлено `UNSAFE ASSEMBLY` разрешений в базе данных master. Дополнительные сведения см. в разделе [строгой безопасности CLR](../database-engine/configure-windows/clr-strict-security.md).  
- График возможности баз данных для моделирования связей многие ко многим "". Сюда входят новые [CREATE TABLE](../t-sql/statements/create-table-sql-graph.md) синтаксис для создания узла и Краевые таблицы и ключевое слово [соответствия](../t-sql/queries/match-sql-graph.md) для запросов. Дополнительные сведения см. в разделе [Graph обработка с помощью 2017 г. SQL Server](../relational-databases/graphs/sql-graph-overview.md).   
- Автоматической настройки является функцией базы данных, которая обеспечивает анализ запроса потенциальных проблем с производительностью, он может рекомендовать решений и автоматически исправить определенные проблемы. Автоматической настройки [!INCLUDE[ssnoversion](../includes/ssnoversion.md)], уведомляет о том, при обнаружении потенциальных проблем производительности, а также позволяет применять действия по исправлению или позволяет [!INCLUDE[ssde](../includes/ssde-md.md)] автоматически устранить проблемы с производительностью. Дополнительные сведения см. в разделе [автоматической настройки](../relational-databases/automatic-tuning/automatic-tuning.md).  
-    Пакетного режима адаптивной присоединение к повысить качество плана (под совместимости db 140).
-    Поочередное исполнение для нескольких инструкций T-SQL возвращающие для повышения качества плана (под совместимости db 140).
- Хранилище запросов сейчас также отслеживает сводные данные статистики ожидания. Отслеживание категории статистики ожидания запроса в хранилище запросов позволяет следующий уровень производительности, устранении неполадок, предоставляя, еще более понять его узких мест, сохраняя ключевых преимуществ хранилище запросов и производительность рабочей нагрузки.
- Поддержка DTC для группы доступности AlwaysOn все межбазовые транзакции между базами данных, которые являются частью группы доступности, в том числе для баз данных, которые являются частью того же экземпляра. Дополнительные сведения см. в разделе [транзакции - группы доступности AlwaysOn и зеркального отображения базы данных](../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)
- Новый столбец **modified_extent_page_count** впервые появился в [sys.dm_db_file_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md) для отслеживания разностных изменений в каждый файл базы данных из базы данных.
- [SELECT INTO](../t-sql/queries/select-into-clause-transact-sql.md) теперь поддерживает загрузку таблицы в файловой группе, кроме файловую группу по умолчанию для пользователя с помощью **ON** ключевое слово.
- Программа установки SQL Server поддерживает указание размер файла начальной базы данных tempdb до **256 ГБ (262 144 МБ)** каждого файла с предупреждением, если размер файла задано значение больше, чем **1 ГБ** и если IFI не включена.
- Новый динамическое административное представление (DMV) [sys.dm_tran_version_store_space_usage](../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-space-usage.md) появилась возможность отслеживать использование хранилища версии каждой базы данных.
- Новое динамическое административное Представление [sys.dm_db_log_info](../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) вводится для предоставления информации виртуального файла Журнала, аналогично DBCC LOGINFO.
- DBCC CLONEDATABASE будут удалены статистики времени выполнения во время клонирования, чтобы не упустить статистики времени выполнения хранилища запросов в базе данных клоне. Помимо этого инструкция DBCC CLONEDATABASE улучшить для поддержки и клонировать полнотекстовых индексов.
- Темпоральные таблицы с системным управлением версиями теперь поддерживают КАСКАДНОГО удаления и CASCADE UPDATE.
- Эта CTP-версия содержит исправления ошибок для ядра СУБД.
- Подробный список 2017 г. усовершенствования CTP-версии в предыдущих выпусках CTP-версии, в разделе [новые возможности SQL Server 2017 г. (компонент Database Engine)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).   

### <a name="sql-server-machine-learning-services"></a>Изучение служб машины SQL Server
- SQL Server R Services имеет новое имя, чтобы отразить поддержку языка Python в CTP-версии 2.0. Теперь можно использовать обучения машины службы (в базе данных) для SQL Server для запуска сценариев R или Python в SQL Server. Или установите Microsoft машины обучения Server (изолированный) для развертывания и использования моделей R и Python, не требующих SQL Server. 
- Обе эти платформы включают новые алгоритмы MicrosoftML для распределенных машинного обучения, а также последнюю версию Microsoft R (версия 9.1.0).
- Дополнительные сведения см. в разделе [новые возможности для машинного обучения](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-2017-ctp-14-march-2017"></a>Новые возможности SQL Server CTP 2017 г. 1.4 (март 2017 г.)
### <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine
- В этой CTP-версии нет новых функций ядра СУБД.
- Эта CTP-версия содержит исправления ошибок для ядра СУБД.
- Подробный список 2017 г. усовершенствования CTP-версии в предыдущих выпусках CTP-версии, в разделе [новые возможности SQL Server 2017 г. (компонент Database Engine)](../database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md).

### <a name="sql-server-r-services"></a>Службы R SQL Server
- В этой CTP-версии нет новых функций служб R.
- Более подробные сведения о новых возможностях служб R, включая сведения для предыдущих CTP-версий, см. в разделе [Новые возможности служб R SQL Server](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md).  

### <a name="sql-server-reporting-services-ssrs"></a>Службы SQL Server Reporting Services (SSRS)
- В этой CTP-версии нет новых функций служб SSRS.
- Более подробные сведения о новых возможностях SSRS, включая сведения из предыдущих выпусков, см. в статье [Новые возможности служб Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 

### <a name="sql-server-analysis-services-ssas"></a>Службы SQL Server Analysis Services (SSAS)
- В этой CTP-версии нет новых функций SSAS.  
- Подробные сведения, включая новые возможности для служб Analysis Services в последних выпусках предварительной версии SSDT и SSMS [новые возможности 2017 г Analysis Services](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md).  

### <a name="sql-server-integration-services-ssis"></a>Службы SQL Server Integration Services
- В этой CTP-версии нет новых функций служб SQL Server Integration Services.
- Более подробные служб SSIS новые сведения, включая сведения из предыдущей CTP-версии, видят [новые возможности интеграции служб 2017 г.](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md).  

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-2017-ctp-13-february-2017"></a>Новые возможности SQL Server CTP 2017 г. 1.3 (февраля 2017 г.)
### <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine
- Повышена производительность косвенных контрольных точек.
- Добавлена поддержка групп доступности без кластеризации.
- Добавлен параметр групп доступности для фиксации минимальных реплик.
- Теперь группы доступности могут работать как в Windows, так и в Linux, что обеспечивает возможность кроссплатформенной миграции и тестирования.
- Добавлена поддержка темпоральных политикой сохранения таблицы. Дополнительные сведения см. в разделе [управление хранением данных журнала в Темпоральных таблицах с системным управлением версиями](../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md#using-temporal-history-retention-policy-approach).
- Реализовано новое динамическое административное представление SYS.DM_DB_STATS_HISTOGRAM.
- Online некластеризованный columnstore построения индекса и перестройте добавлена поддержка
- Реализованы пять новых динамических административных представлений для возврата данных о процессе Linux. Дополнительные сведения см. в статье [Динамические административные представления процессов Linux (Transact-SQL)](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- Добавлено представление[sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) для проверки статистики.

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>Службы SQL Server Analysis Services (SSAS) (CTP 1.3)
- Подсказки службы кодирования — расширенная функция, использующаяся для оптимизации обработки (обновления данных) больших табличных моделей в памяти. Дополнительные сведения см. в разделе [новые возможности 2017 г Analysis Services](../analysis-services/what-s-new-in-sql-server-analysis-services-2017.md). 


![horizontal_bar](../sql-server/media/horizontal-bar.png)

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Общение с командой разработчиков SQL Server 
- [Stack Overflow (тег sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [Форумы MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect — сообщайте об ошибках и запрашивайте функции](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit — общее обсуждение по поводу R](https://www.reddit.com/r/SQLServer/)

## <a name="see-also"></a>См. также:    
- ![Заметки о выпуске](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) [заметки о выпуске SQL Server 2017 г](../sql-server/sql-server-2017-release-notes.md). 
- [Возможности, поддерживаемые различными выпусками](https://msdn.microsoft.com/library/cc645993.aspx)
- [Требования к оборудованию и программному обеспечению для установки](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
- [Мастер установки SQL Server](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)
- [Установка обновлений для обслуживания SQL Server](http://msdn.microsoft.com/library/6df72a78-6b36-4bc1-948e-04b4ebe46094)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)

