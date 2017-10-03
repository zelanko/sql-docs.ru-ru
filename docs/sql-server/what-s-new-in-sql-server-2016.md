---
title: "Что нового в SQL Server 2016"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/21/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "новая версия sql server"
helpviewer_keywords:
- new features [SQL Server]
- SQL Server, what's new
- SQL Server 2008 what's new
- what's new [SQL Server]
ms.assetid: 6a428023-e3cc-4626-a88a-4c13ccbd7db0
caps.latest.revision: 224
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 2ef79a82259dee5a8767b382ca5ddaa0795dab7e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="whats-new-in-sql-server-2016"></a>Что нового в SQL Server 2016
 Благодаря SQL Server 2016 вы сможете создавать важные аналитические приложения с помощью масштабируемой гибридной платформы баз данных, в которую уже встроено все необходимое — от возможностей эффективной обработки в памяти и повышенной безопасности до функций аналитики в базе данных. В выпуске SQL Server 2016 добавлены новые средства безопасности, возможности выполнения запросов, интеграции Hadoop, облачной интеграции, аналитики R, а также множество других усовершенствований. 

На этой странице представлен краткий обзор новых возможностей и ссылки на подробные сведения о них для каждого компонента SQL Server 2016. 

![SQL Server 2016](../sql-server/media/sql-server-2016.png) 

 **Оцените SQL Server уже сегодня!** 
- Скачайте **бесплатный** [**выпуск SQL Server 2016 Developer Edition**](https://www.microsoft.com/en-us/cloud-platform/sql-server-editions-developers).
- Скачайте последнюю версию [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md). 
- Есть учетная запись Azure? Запустите [виртуальную машину с уже установленным решением SQL Server 2016](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/).

## <a name="sql-server-2016-database-engine"></a>Ядро СУБД SQL Server 2016
- Теперь вы можете настроить **несколько файлов базы данных tempDB** во время установки и настройки SQL Server.
- В базе данных нового **хранилища запросов** хранятся тексты запросов, планы выполнения и метрики производительности. Это позволяет легко выполнять мониторинг и устранять проблемы с производительностью. На панели мониторинга указано, какие запросы потребляют больше всего времени, памяти или ресурсов ЦП.
- **Темпоральные таблицы** — это хронологические таблицы, в которые записываются все изменения данных, а также дата и время таких изменений.
- Новые встроенные средства **поддержки JSON** в SQL Server обеспечивают импорт, экспорт, синтаксический анализ и хранение файлов JSON.
- Новый обработчик запросов **PolyBase** интегрирует SQL Server с внешними данными в Hadoop или хранилище BLOB-объектов Azure. Теперь вы можете импортировать и экспортировать данные, а также выполнять запросы.
- Новая функция **Stretch Database** позволяет выполнять безопасную динамическую архивацию данных из локальной базы данных SQL Server в базу данных Azure SQL в облаке. SQL Server автоматически обращается к данным в локальных и удаленных связанных базах данных. 
- **Выполняющаяся в памяти OLTP.** 
    - Реализована поддержка FOREIGN KEY, ограничений UNIQUE и CHECK, а также скомпилированных в собственном коде хранимых процедур OR, NOT SELECT DISTINCT, OUTER JOIN и вложенных запросов в SELECT.
    - Поддерживаются таблицы до 2 ТБ (от 256 ГБ). 
    - Усовершенствованы индексы хранилища столбцов для сортировки и поддержки групп доступности AlwaysOn.
- Новые функции безопасности:
    - **Постоянное шифрование.** Если оно включено, доступ к зашифрованным конфиденциальным данным в базе данных SQL Server 2016 получают только приложения с ключом шифрования. Ключ никогда не передается в SQL Server.
    - **Динамическое маскирование данных.** Если этот параметр указан в определении таблицы, маскированные данные будут скрыты от большинства пользователей, полностью отображаясь только для пользователей с разрешением UNMASK.
    - **Безопасность на уровне строк.** Доступ к данным можно ограничить на уровне ядра СУБД, и для пользователей будет отображаться только релевантная информация. 

См. раздел о [ядре СУБД](../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md).
## <a name="sql-server-2016-analysis-services-ssas"></a>SQL Server 2016 Analysis Services (SSAS)
Службы SQL Server 2016 Analysis Services повышают производительность, расширяют возможности разработки, управления базами данных, фильтрации и обработки, а также предоставляют много других преимуществ для табличных баз данных на **уровне совместимости 1200**.
- **[Службы R SQL Server](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md)** интегрируют язык R, используемый для статистического анализа в SQL Server. 
- Новое **средство проверки согласованности базы данных (DBCC)** выполняется для внутренних целей при обнаружении возможных проблем с повреждением данных.
- **Прямой запрос**, выполняющийся перед импортом динамических внешних данных, теперь поддерживает дополнительные источники данных, включая Azure SQL, Oracle и Teradata. 
- Реализовано множество новых **функций DAX (выражения доступа к данным)**.
- Новое пространство имен **[Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx)** управляет экземплярами и моделями в табличном режиме. 
- [Управляющие объекты службы Analysis Services (AMO)](http://msdn.microsoft.com/library/mt436122.aspx) переработаны и теперь содержат вторую сборку — **Microsoft.AnalysisServices.Core.dll**.

См. раздел о [подсистеме служб Analysis Services (SSAS)](../analysis-services/what-s-new-in-analysis-services.md). 

## <a name="sql-server-2016-integration-services-ssis"></a>SQL Server 2016 Integration Services (SSIS)
- Поддержка **групп доступности AlwaysOn**
- **Добавочное развертывание пакетов**
- Поддержка **Always Encrypted**
- Новая роль уровня базы данных **ssis_logreader**
- Новый уровень **настраиваемого протоколирования**
- **Имена столбцов для ошибок** в потоке данных 
- Новые **соединители**
- Поддержка **файловой системы Hadoop (HDFS)**

См. раздел о [службах Integration Services (SSIS)](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md).

## <a name="sql-server-2016-master-data-services-mds"></a>Службы SQL Server 2016 Master Data Services (MDS)
- **Улучшения в производной иерархии**, включая поддержку для рекурсивных иерархий и иерархий "многие ко многим"
- Фильтрация **атрибута на основе домена**
- **Синхронизация сущностей** для совместного использования данных сущности в разных моделях
- Рабочие процессы утверждения с использованием **наборов изменений**
- **Пользовательские индексы** для повышения производительности запросов
- Новые **уровни разрешений** для повышения уровня безопасности
- Переработанный интерфейс **управления бизнес-правилами**

См. раздел о [службах Master Data Services (MDS)](../master-data-services/what-s-new-in-master-data-services-mds.md).

## <a name="sql-server-2016-reporting-services-ssrs"></a>Службы SQL Server 2016 Reporting Services (SSRS)
Этот выпуск служб Reporting Services тщательно переработан корпорацией Майкрософт. 
- Новый **портал веб-отчетов** с функцией ключевых показателей эффективности
- Новый **издатель мобильных отчетов**
- **Переработанный механизм визуализации отчетов** с поддержкой HTML5 
- Новые **типы диаграмм**: "дерево" и "солнечные лучи" 

См. раздел о [службах Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).

## <a name="next-steps"></a>Следующие шаги   
- [Установка SQL Server](../database-engine/install-windows/installation-for-sql-server-2016.md)   
- [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md) 
- [Таблица SQL Server 2016](http://download.microsoft.com/download/C/5/3/C53C3AEF-653C-4598-8721-D522E8AC6A3A/SQL_Server_2016_Everything_Built-In_Datasheet_EN_US.pdf)
- [Возможности, поддерживаемые различными выпусками SQL Server](https://msdn.microsoft.com/library/cc645993.aspx)
- [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
- [Установка SQL Server 2016 с помощью мастера установки](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)
- [Настройка и обслуживание установки](http://msdn.microsoft.com/library/6df72a78-6b36-4bc1-948e-04b4ebe46094)    
- [New SQL PowerShell module](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update/)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
