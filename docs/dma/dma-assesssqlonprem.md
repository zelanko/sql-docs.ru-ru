---
title: Провести оценку миграции сервера S'L
titleSuffix: Data Migration Assistant
description: Узнайте, как использовать помощника по миграции данных для оценки внутреннего сервера S'L перед переходом на другой сервер S'L или в базу данных Azure S'L
ms.date: 01/15/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: 59dc8c96ebda5ac66fb6701d480cb6d633e83158
ms.sourcegitcommit: 48e259549f65f0433031ed6087dbd5d9c0a51398
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2020
ms.locfileid: "80809753"
---
# <a name="perform-a-sql-server-migration-assessment-with-data-migration-assistant"></a>Выполнение оценки переноса SQL Server с использованием Помощника по миграции данных

Следующие пошаговые инструкции помогут вам провести первую оценку для перехода на внутренний сервер S'L Server, сервер S'L, работающий на Базе данных Azure VM, или базу данных Azure S'L с помощью помощи по миграции данных.

   > [!NOTE]
   > Помощник по миграции данных v5.0 вводит поддержку для анализа подключения к базе данных и встроенных запросов в код приложения. Для получения дополнительной информации смотрите запись в блоге [с помощью помощника по миграции данных для оценки уровня доступа к данным приложения.](https://techcommunity.microsoft.com/t5/Microsoft-Data-Migration/Using-Data-Migration-Assistant-to-assess-an-application-s-data/ba-p/990430)

## <a name="create-an-assessment"></a>Создание оценки

1. Выберите **значок «Новый»** — значок «Новая» и затем выберите тип проекта **«Оценка».**

2. Укажите тип исходного и целевого серверов.

    Если вы модернизируете свой предприимчовый экземпляр S'L Server до современного предпосылок s-L Server или до сервера S'L, размещенного на Azure VM, установите исходный и целевой тип сервера на **сервер S'L Server.** Если вы перебрались в базу данных Azure S'L, вместо этого установите тип целевого сервера в **базу данных Azure S'L.**

3. Нажмите кнопку **Создать**.

   ![Создание оценки](../dma/media/dma-assesssqlonprem/new-assessment.png)

## <a name="choose-assessment-options"></a>Выберите варианты оценки

1. Выберите целевую версию сервера S'L, к которой планируется миграция.

2. Выберите тип отчета.

   При оценке исходного экземпляра S'L Server для перехода на внутренний сервер S'L Или или на сервер S'L, размещенный на целевых показателях Azure VM, вы можете выбрать один или оба из следующих типов отчетов об оценке:

    - **Вопросы совместимости**
    - **Рекомендация новых функций**

   ![Выберите тип отчета об оценке для целевой цели сервера S'L](../dma/media/dma-assesssqlonprem/assessment-types.png)

   При оценке исходного экземпляра S'L Server для перехода в базу данных Azure S'L можно выбрать один или оба из следующих типов отчетов об оценке:

    - **проверка совместимости базы данных;**
    - **проверка четности компонентов.**

    ![Выберите тип отчета об оценке для целевой базы данных S'L](../dma/media/dma-assesssqlonprem/assessment-types-azure.png)

## <a name="add-databases-and-extended-events-trace-to-assess"></a>Добавление баз данных и расширенных событий для оценки

1. Выберите **Добавить Источники,** чтобы открыть меню вылет соединения.

2. Введите имя экземпляра сервера S'L, выберите тип аутентификации, установите правильные свойства соединения, а затем выберите **Connect.**

3. Выберите базы данных для оценки, а затем выберите **Добавить**.

    > [!NOTE]
    > Вы можете удалить несколько баз данных, выбрав их при хранении ключа Shift или Ctrl, а затем нажав **удалить источники.** Вы также можете добавить базы данных из нескольких экземпляров сервера S'L, выбрав **источники**добавления.

4. Если у вас есть какие-либо специальные или динамические запросы s-L или любые dML-выписки, инициированные через слой данных приложения, введите путь к папке, в которой вы разместили все собранные файлы сеанса расширенных событий, которые были собраны для захвата рабочей нагрузки на исходном сервере S'L.

     В следующем примере показано, как создать расширенную сессию событий на исходном сервере S'L Server для захвата рабочей нагрузки уровня данных приложения.  Захват рабочей нагрузки на время, которое представляет вашу пиковую рабочую нагрузку.

    ```
    DROP EVENT SESSION [DatalayerSession] ON SERVER
    go
    CREATE EVENT SESSION [DatalayerSession] ON SERVER  
    ADD EVENT sqlserver.sql_batch_completed( 
        ACTION (sqlserver.sql_text,sqlserver.client_app_name,sqlserver.client_hostname,sqlserver.database_id))
    ADD TARGET package0.asynchronous_file_target(SET filename=N'C:\temp\Demos\DataLayerAppassess\DatalayerSession.xel')  
    WITH (MAX_MEMORY=2048 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=3 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=OFF)
    go
    ---Start the session
    ALTER EVENT SESSION [DatalayerSession]
          ON SERVER
        STATE = START;
    ---Wait for few minutes
    
    ---Query events
        
        SELECT 
        object_name,
        CAST(event_data as xml) as event_data,
        file_name, 
        file_offset
    FROM sys.fn_xe_file_target_read_file('C:\temp\Demos\DataLayerAppassess\DatalayerSession*xel', 
                'C:\\temp\\Demos\\DataLayerAppassess\\DatalayerSession*xem', 
                null,
                null)
    ---Stop the session after capturing the peak load.
    ALTER EVENT SESSION [DatalayerSession]
          ON SERVER
        STATE = STOP;
        
        go
    ```

5. Нажмите кнопку **Далее** для запуска оценки.

    ![Добавление источников и начало оценки](../dma/media/dma-assesssqlonprem/select-database1.png)

> [!NOTE]
> Вы можете одновременно выполнить несколько оценок и просмотреть их состояние, открыв страницу **​All Assessments** (Все оценки).

## <a name="view-results"></a>Просмотр результатов

Продолжительность оценки зависит от количества добавленных баз данных и размера схемы каждой базы данных. Результаты отображаются для каждой базы данных, как только они доступны.

1. Выберите базу данных, которая завершила оценку, а затем переключитесь между **проблемами совместимости** и **рекомендациями функций** с помощью коммутатора.

2. Просмотрите проблемы совместимости во всех уровнях совместимости, поддерживаемых целевой версией s'L Server, выбранной на странице **Options.**

Вы можете просмотреть проблемы совместимости, проанализировав затронутый объект, его детали и, возможно, исправление каждой проблемы, выявленной в соответствии с **изменениями Breaking,** **Behavior changes**и **Deprecated.**

![Просмотр результатов оценки](../dma/media/dma-assesssqlonprem/review-results.png)

Аналогичным образом можно просмотреть рекомендацию функции в областях **производительности,** **хранения**и **безопасности.**

Рекомендации по функциям охватывают различные виды функций, таких как In-Memory OLTP, Columnstore, Stretch Database, Always Encrypted, Dynamic Data Masking и Transparent Data Encryption.

![Просмотр рекомендаций функций](../dma/media/dma-assesssqlonprem/feature-recommendations.png)

Для базы данных Azure S'L оценки предоставляют проблемы блокировки миграции и проблемы паритета функций.Просмотрите результаты для обеих категорий, выбрав конкретные варианты.

- Категория **паритета функций S'L Server** предоставляет полный набор рекомендаций, альтернативные подходы, доступные в Azure, и смягчающие шаги. Это поможет вам спланировать эти усилия в ваших миграционных проектах.

  ![Просмотр информации для паритета функций сервера S'L](../dma/media/dma-assesssqlonprem/sql-feature-parity.png)

- Категория **проблем совместимости** предоставляет частично поддерживаемые или неподдерживаемые функции, которые блокируют миграцию баз данных на местах в базы данных S'L Server в базы данных Azure S'L.Затем он предоставляет рекомендации, которые помогут вам решить эти вопросы.

  ![Просмотр проблем совместимости](../dma/media/dma-assesssqlonprem/compatibility-issues.png)

## <a name="assess-a-data-estate-for-target-readiness"></a>Оценка хранилища данных для целевой готовности

Если вы хотите расширить эти оценки на весь объем данных и найти относительную готовность экземпляров и баз данных сервера S'L для миграции в базу данных Azure S'L, загрузите результаты в концентратор Azure Migrate, выбрав **Upload to Azure Migrate.**

Это позволяет просматривать консолидированные результаты по проекту концентратора Azure Migrate.

Подробные, пошаговые рекомендации по оценке целевой готовности доступны [здесь.](https://docs.microsoft.com/sql/dma/dma-assess-sql-data-estate-to-sqldb?view=sql-server-2017)

   ![Загрузка результатов в Azure Migrate](../dma/media/dma-assesssqlonprem/upload-to-azure-migrate.png)

## <a name="export-results"></a>Экспорт результатов

После того, как все базы данных завершат оценку, выберите **отчет Экспорта** для экспорта результатов либо в файл JSON, либо в файл CSV. Затем вы можете анализировать данные в удобное для вас время.

## <a name="save-and-load-assessments"></a>Сохранение и загрузка оценок

В дополнение к экспорту результатов оценки можно сохранить детали оценки в файл и загрузить файл оценки для последующего рассмотрения.  Для получения дополнительной информации см. [Save and load assessments with Data Migration Assistant](../dma/dma-save-load-assessments.md)
