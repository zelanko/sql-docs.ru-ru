---
title: Обновленные документы по SSMS для SQL Server | Документация Майкрософт
description: Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Management Studio (SSMS) для Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: ssms
ms.date: 02/03/2018
ms.openlocfilehash: f282e36152697b906b2d4e115be26943ae014fd9
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2018
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Новые и недавно обновленные: SQL Server Management Studio (SSMS) для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **03.12.2017**&nbsp;–&nbsp;**03.02.2018**
- *Предметная область:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Установка локализованных версий SQL Server Management Studio (SSMS)](install-other-languages.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Скачивание SQL Server Management Studio (SSMS)](#TitleNum_1)
2. [Среда SQL Server Management Studio (SSMS) — журнал изменений](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-sql-server-management-studio-ssmsdownload-sql-server-management-studio-ssmsmd"></a>1. &nbsp; [Скачивание SQL Server Management Studio (SSMS)](download-sql-server-management-studio-ssms.md)

*Обновление: 18.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 83.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0e123e7bdf04f02fcd26ac31fa30ed5f31b19c7d 924246b55d3cad6a5d068da8a41f4be23dcfeb2b  (PR=4652  ,  Filename=download-sql-server-management-studio-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



SSMS 17.4 — это новейшая версия SQL Server Management Studio. Поколение 17.x среды SSMS поддерживает почти все функциональные возможности выпусков SQL Server 2008 — SQL Server 2017. Версия 17.x также поддерживает SQL Analysis Services в режиме PaaS.

Версия 17.4 включает следующее.

Оценка уязвимостей:
- Добавлена новая служба оценки уязвимости SQL, которая проверяет базы данных на наличие потенциальных уязвимостей и отклонений от рекомендаций, например неверных настроек, избыточных разрешений и незащищенных конфиденциальных данных.
- Результаты оценки включают в себя практические действия по устранению каждой проблемы, а также настроенные скрипты исправления, если это возможно. Отчет об оценке можно настроить для конкретной среды и конкретных требований. Дополнительные сведения об [оценке уязвимостей SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO:
- Исправлена проблема, из-за которой свойство *HasMemoryOptimizedObjects* вызывало исключение в Azure.
- Добавлена поддержка новой функции CATALOG_COLLATION.

Панель мониторинга AlwaysOn:
- Усовершенствован анализ задержек в группах доступности.
- Добавлены два новых отчета: *AlwaysOn\_Latency\_Primary* и *AlwaysOn\_Latency\_Secondary*.

Showplan
- Обновленные ссылки указывают на правильную документацию.
- Анализ отдельного плана выполняется непосредственно на основе фактического плана.
- Создан новый набор значков.
- Добавлена поддержка для распознания логических операторов применения, например GbApply, InnerApply.

XE Profiler:
- Переименован в XEvent Profiler.
- Теперь при помощи команд меню для остановки и запуска сеанс останавливается и запускается по умолчанию.
- Включена поддержка сочетаний клавиш (например, CTRL+F для поиска).
- Добавлены действия database\_name и client\_hostname для соответствующих событий в сеансах XEvent Profiler. Чтобы изменения вступили в силу, возможно, потребуется удалить существующие экземпляры сеансов QuickSessionStandard или QuickSessionTSQL на серверах. Дополнительные сведения см. на странице [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981).



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>2. &nbsp; [Среда SQL Server Management Studio (SSMS) — журнал изменений](sql-server-management-studio-changelog-ssms.md)

*Обновлено: 29.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1))

<!-- Source markdown line 27.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5096fa8f1ae3f2e4bc040f43cb8810d96f2c69c eb641ac39386a26a76dc303f5bd55eb3f9f4c78d  (PR=0  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=ba4b1c2e5200f2f78786b710da18fd38fedde6c9) -->



**[SSMS 17.4](download-sql-server-management-studio-ssms.md)**

Общедоступная версия | Номер сборки: 14.0.17213.0

**Новые возможности**


**Общие ошибки SSMS**

Оценка уязвимостей:
- Добавлена новая служба оценки уязвимости SQL, которая проверяет базы данных на наличие потенциальных уязвимостей и отклонений от рекомендаций, например неверных настроек, избыточных разрешений и незащищенных конфиденциальных данных.
- Результаты оценки включают в себя практические действия по устранению каждой проблемы, а также настроенные скрипты исправления, если это возможно. Отчет об оценке можно настроить для конкретной среды и конкретных требований. Дополнительные сведения об [оценке уязвимостей SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO:
- Исправлена проблема, из-за которой свойство *HasMemoryOptimizedObjects* вызывало исключение в Azure.
- Добавлена поддержка новой функции CATALOG_COLLATION.

Панель мониторинга AlwaysOn:
- Усовершенствован анализ задержек в группах доступности.
- Добавлены два новых отчета: *AlwaysOn\_Latency\_Primary* и *AlwaysOn\_Latency\_Secondary*.

Showplan
- Обновленные ссылки указывают на правильную документацию.
- Анализ отдельного плана выполняется непосредственно на основе фактического плана.
- Создан новый набор значков.
- Добавлена поддержка для распознания логических операторов применения, например GbApply, InnerApply.

XE Profiler:
- Переименован в XEvent Profiler.
- Теперь при помощи команд меню для остановки и запуска сеанс останавливается и запускается по умолчанию.
- Включена поддержка сочетаний клавиш (например, CTRL+F для поиска).
- Добавлены действия database\_name и client\_hostname для соответствующих событий в сеансах XEvent Profiler. Чтобы изменения вступили в силу, возможно, потребуется удалить существующие экземпляры сеансов QuickSessionStandard или QuickSessionTSQL на серверах. Дополнительные сведения см. на странице [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981).

Командная строка:
- Добавлен новый параметр командной строки (-G), с помощью которого SSMS может автоматически подключаться к серверу или базе данных с использованием аутентификации Active Directory (встроенная аутентификация или аутентификация с помощью пароля). Дополнительные сведения см. в статье [Программа SSMS](ssms-utility.md).







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи


- [Новые + обновленные (1+3):&nbsp; **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (0+1):&nbsp; **Analytics Platform System для SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (0+1):&nbsp; **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+1):&nbsp; **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (12+1): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (6+2):&nbsp; **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (15+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (2+9):&nbsp; **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (1+0):&nbsp; **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (1+1):&nbsp; **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(1+1):&nbsp; **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1):&nbsp; **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (1+2):&nbsp; **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2):&nbsp; **Transact-SQL**](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи


- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../samples/new-updated-samples.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


