---
title: Обновленные документы по T-SQL | Документы Майкрософт
description: Отрывки из недавно обновленного содержимого в документации по Transact-SQL.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: t-sql
ms.date: 04/28/2018
ms.openlocfilehash: b1bc891bf7edc4cd82c38c8d647c279828190298
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Новые и недавно обновленные: документы по Transact-SQL



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Даты обновлений:* &nbsp; **02.03.2018**&nbsp;–&nbsp;**28.04.2018**
- *Предметная область:* &nbsp; **T-SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


***На данный момент новых статей нет.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](#TitleNum_1)
2. [Инструкции RESTORE (Transact-SQL)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-alter-database-scoped-configuration-transact-sqlstatementsalter-database-scoped-configuration-transact-sqlmd"></a>1. &nbsp; [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](statements/alter-database-scoped-configuration-transact-sql.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 150.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f6833910b664d0059a9073589807b195052325b3 bf969f123b22e6ebc650380a6905156f26ed6ca6  (PR=0  ,  Filename=alter-database-scoped-configuration-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



XTP_PROCEDURE_EXECUTION_STATISTICS  **=** { ON | **OFF** }

**Область применения**: *{укажите_включенный_контент}*

Включает или отключает сбор статистики выполнения на уровне модуля для скомпилированных в собственном коде модулей T-SQL в текущей базе данных. Значение по умолчанию — OFF. Статистика выполнения отражается в [sys.dm_exec_procedure_stats].

Статистика выполнения на уровне модуля для скомпилированных в собственном коде модулей T-SQL собирается либо при значении ON этого параметра, либо если сбор статистики включен с помощью [sp_xtp_control_proc_exec_stats].

XTP_QUERY_EXECUTION_STATISTICS  **=** { ON | **OFF** }

**Область применения**: *{укажите_включенный_контент}*

Включает или отключает сбор статистики выполнения на уровне инструкций для скомпилированных в собственном коде модулей T-SQL в текущей базе данных. Значение по умолчанию — OFF. Статистика выполнения отражается в [sys.dm_exec_query_stats] и в [хранилище запросов].

Статистика выполнения на уровне инструкций для скомпилированных в собственном коде модулей T-SQL собирается либо при значении ON этого параметра, либо если сбор статистики включен с помощью [sp_xtp_control_query_exec_stats].

Дополнительные сведения о мониторинге производительности скомпилированных в собственном коде модулей T-SQL см. в разделе [Мониторинг производительности скомпилированных в собственном коде хранимых процедур].



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-restore-statements-transact-sqlstatementsrestore-statements-transact-sqlmd"></a>2. &nbsp; [Инструкции RESTORE (Transact-SQL)](statements/restore-statements-transact-sql.md)

*Обновлено: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1))

<!-- Source markdown line 339.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2902efb58bb964d3e9a0660956690d37f0397c00 36186a7cffd26ffa54a83e383ffd752dbc568a4d  (PR=0  ,  Filename=restore-statements-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Общие примечания — управляемый экземпляр базы данных SQL**


Асинхронное восстановление будет продолжаться даже в случае разрыва соединения с клиентом. В случае разрыва соединения вы можете просмотреть состояние операции восстановления (а также инструкций CREATE и DROP для базы данных) в представлении [sys.dm_operation_status].

Следующие параметры базы данных устанавливаются или переопределяются и в последующем не могут быть изменены:

- NEW_BROKER (если брокер не включен в BAK-файле)
- ENABLE_BROKER (если брокер не включен в BAK-файле)
- AUTO_CLOSE=OFF (если для базы данных в BAK-файле установлен параметр AUTO_CLOSE=ON)
- RECOVERY FULL (если для базы данных в BAK-файле установлен режим восстановления SIMPLE или BULK_LOGGED)
- Добавляется оптимизированная для операций в памяти файловая группа с названием XTP (если она отсутствовала в исходном BAK-файле). Любые существующие оптимизированные для операций в памяти файловые группы переименовываются в XTP
- Параметры SINGLE_USER и RESTRICTED_USER преобразуются в MULTI_USER

**Ограничения — управляемый экземпляр базы данных SQL**

Применяются следующие ограничения:

- BAK-файлы, содержащие несколько резервных наборов данных, не могут быть восстановлены.
- BAK-файлы, содержащие несколько файлов журнала, не могут быть восстановлены.
- Если BAK-файл содержит данные FILESTREAM, восстановление завершится сбоем.
- На данный момент невозможно восстановление резервных копий, которые содержат базы данных с активными объектами для выполнения в памяти.
- В настоящее время невозможно восстановление резервных копий, содержащих базы данных, в которых в какой-то момент времени существовали объекты для выполнения в памяти.
- На данный момент невозможно восстановление резервных копий, которые содержат базы данных, находящиеся в режиме только для чтения. В ближайшее время эти ограничения будут устранены.

Дополнительные сведения см. в разделе [Управляемый экземпляр]







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи

- [Новые + обновленные (11+6): &nbsp; &nbsp;**Углубленная аналитика для SQL** (документация)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (18+0): &nbsp;&nbsp;**Analysis Services для SQL** (документация)](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (218+14):  **Подключение к SQL** (документация)](../connect/new-updated-connect.md)
- [Новые + обновленные (14+0): &nbsp; &nbsp;**Ядро СУБД для SQL** (документация)](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (3+2): &nbsp; &nbsp;**Integration Services для SQL** (документация)](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (3+3): &nbsp; &nbsp;**Linux для SQL** (документация)](../linux/new-updated-linux.md)
- [Новые + обновленные (7+10): &nbsp; &nbsp;**Реляционные базы данных для SQL** (документация)](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (0+2): &nbsp; **&nbsp;Reporting Services для SQL** (документация)](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (1+3): &nbsp; &nbsp;**SQL Operations Studio** (документация)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(2+3): &nbsp; &nbsp;**Microsoft SQL Server** (документация)](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (1+1): &nbsp; &nbsp;**SQL Server Data Tools (SSDT)** (документация)](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (5+2): &nbsp; &nbsp;**SQL Server Management Studio (SSMS)** (документация)](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2): &nbsp; &nbsp;**Transact-SQL** (документация)](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (1+1): &nbsp;**&nbsp;Инструменты для SQL** (документация)](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0):  **Analytics Platform System для SQL** (документация)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../samples/new-updated-samples.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)

