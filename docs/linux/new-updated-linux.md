---
title: "Обновлено - SQL Server в Linux docs | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации Microsoft SQL Server в Linux."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: linux
ms.date: 02/03/2018
ms.openlocfilehash: fc740b59397f0438a059b38df57ffc40999cc81e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Обновление новых и недавно: SQL Server в Linux документы



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2017 г-12-03** &nbsp; - в - &nbsp; **2018-02-03**
- *Предметной области:* &nbsp; **Microsoft SQL Server в Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Настройка несколькими подсетями группы доступности AlwaysOn и экземпляров отказоустойчивых кластеров](sql-server-linux-configure-multiple-subnet.md)
2. [Создание и настройка группы доступности для SQL Server в Linux](sql-server-linux-create-availability-group.md)
3. [Развертывание кластера Pacemaker для SQL Server в Linux](sql-server-linux-deploy-pacemaker-cluster.md)
4. [SQL Server в Linux, часто задаваемые вопросы (FAQ)](sql-server-linux-faq.md)
5. [Основные сведения о доступности SQL Server для Linux развертываний](sql-server-linux-ha-basics.md)
6. [Настройка SQL Server контейнер в Kubernetes для обеспечения высокой доступности](tutorial-sql-server-containers-kubernetes.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Всегда в группах доступности в Linux](#TitleNum_1)
2. [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-always-on-availability-groups-on-linuxsql-server-linux-availability-group-overviewmd"></a>1. &nbsp;[Всегда в группах доступности в Linux](sql-server-linux-availability-group-overview.md)

*Обновлено: 2018-01-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 85.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 85685bc8ad3528aa26ca3f2bba7b0112808ad6f9 51aff6e55104c8f775d2b4f4461e44f689a9ee6b  (PR=4768  ,  Filename=sql-server-linux-availability-group-overview.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=d4d880dd9c247d1e7fb7a728d5231bc9ac61c989) -->



Автоматическое переключение группы Доступности может происходить, когда выполняются следующие условия:

-   Перемещение данных синхронной присваивается первичной и вторичной реплики.
-   Сервер-получатель находится в состоянии синхронизации (не синхронизировано), это означает, что они в той же точке данных.
-   Тип кластера устанавливается к внешним. Автоматический переход на другой ресурс с типом кластера нет невозможна.
-   `sequence_number` Вторичная реплика становится первичной имеет наибольший порядковый номер — другими словами, вторичная реплика `sequence_number` соответствует одному из исходной первичной реплике.

Если эти условия выполняются, сбоя сервера, на котором размещена первичная реплика группы Доступности меняют владельца синхронная реплика. Поведение для синхронных реплик (из которой может быть три общее: основной и двух вторичных реплик) дополнительно может управляться `required_synchronized_secondaries_to_commit`. Работа со и действий в Windows и Linux, но по-разному полностью настроена. В Linux значение автоматически настраивается с кластера на сам ресурс группы Доступности.

**Только для настройки реплики и кворума**


Также новый в 2017 г. SQL Server на определенный момент CU1 — только для настройки реплики. Поскольку Pacemaker отличается от WSFC, особенно в том случае, когда дело доходит до кворума и требовать STONITH, конфигурацию двух узлов будет работать не когда речь заходит о группе Доступности. Для экземпляра отказоустойчивого Кластера кворума механизмы, предоставляемые Pacemaker может быть нормально после того, так как все отработки отказа FCI разрешение конфликтов происходит на уровне кластера. Для группы Доступности в SQL Server, где хранятся все метаданные происходит разрешение конфликтов в Linux. Это происходит, где реплика только для конфигурации вступает в действие.

Без ничего третий узел и по крайней мере один синхронизированной реплики не требуются. Это не будет работать для SQL Server Standard, поскольку он может иметь только двух реплик, участвующих в группе Доступности. Реплика только для конфигурации хранится конфигурация группы Доступности в базе данных master, совпадает с другими элементами конфигурации группы Доступности. Реплика только для конфигурации не имеет пользовательских баз данных, участвующих в группе Доступности. Данные конфигурации передается синхронно с сервера-источника. Эти данные затем используется при отработке отказа, будь то автоматический или ручной.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-extract-transform-and-load-data-on-linux-with-ssissql-server-linux-migrate-ssismd"></a>2. &nbsp;[Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)

*Обновлено: 2018-01-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1))

<!-- Source markdown line 50.  ms.author= lle.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9bba002ae3955ebb8376c7c85b7ec1ac8c706073 1533a8e0bfe553e5404de79129119b3f93185ee9  (PR=4768  ,  Filename=sql-server-linux-migrate-ssis.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=d4d880dd9c247d1e7fb7a728d5231bc9ac61c989) -->



    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Укажите `/de[crypt]` параметр и введите пароль в интерактивном режиме, как показано в следующем примере:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de

    Enter decryption password:
    ```

3.  Укажите `/de` параметр, чтобы предоставить пароль в командной строке, как показано в следующем примере. Этот метод не рекомендуется, поскольку она сохраняет пароль для дешифрования с помощью команды в журнале команд.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test

    Warning: Using /De[crypt] <password> may store decryption password in command history.

    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

**Проектировать пакеты**


**Подключения к источникам данных ODBC**. С помощью служб SSIS на Linux CTP-версии 2.1 обновления и более поздних версий пакетов служб SSIS можно использовать подключения ODBC в Linux. Эта функциональность была протестирована с SQL Server и драйверы MySQL ODBC, но также требуются для работы с любой драйвер ODBC Юникода, отслеживающее спецификации ODBC. Во время разработки укажите имя источника данных или строку подключения для подключения к данным ODBC; Можно также использовать проверку подлинности Windows. Дополнительные сведения см. в разделе [записи блога Представляем поддержка ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).







## <a name="similar-articles-about-new-or-updated-articles"></a>Аналогичные статьи о новых или обновленных статьях

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметной области, *сделать* новыми или были недавно обновлены статьи


- [Новый + обновленные (1 + 3):&nbsp; **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (0 + 1):&nbsp; **Analytics Platform System для SQL** документы](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новый + обновленные (0 + 1):&nbsp; **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (0 + 1):&nbsp; **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (12 + 1): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (6 + 2):&nbsp; **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (15 + 0): **PowerShell для SQL** документы](../powershell/new-updated-powershell.md)
- [Новый + обновленные (2 + 9):&nbsp; **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (1 + 0):&nbsp; **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (1 + 1):&nbsp; **операций SQL Studio** документы](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новый + обновленные (1 + 1):&nbsp; **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (0 + 1):&nbsp; **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (1 + 2):&nbsp; **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (0 + 2):&nbsp; **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметной области, которые выполняют *не* иметь любой новыми или были недавно обновлены статьи


- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новый + обновленные (0 + 0): **объектов данных ActiveX (ADO) для SQL** документы](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../sample/new-updated-sample.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)


