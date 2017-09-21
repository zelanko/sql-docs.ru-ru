---
title: "Обновленные документы по SSDT для SQL Server | Документация Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Data Tools (SSDT) для Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: ssdt-sql-server-data-tools
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 8ae9a49443525524cf7f6ffceba4fb44984c7052
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Новые и недавно обновленные: SQL Server Data Tools (SSDT)



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат выхода обновлений:* &nbsp; **18.07.2017** &nbsp;—&nbsp; **11.09.2017**
- *Предметная область:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [SQL Server Data Tools. Условия лицензии](sql-server-data-tools-license-terms-vs2017.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Журнал изменений для SQL Server Data Tools (SSDT)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1. &nbsp; [Журнал изменений для SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Обновлено: 23.08.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 23.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 536fe0fe41b023a4186f494a509fa14fcbafccf4 e5bc7b76c1755f5a1af77f6cd63d8e8691dafe7b  (PR=2927  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=71a2cbf181c94c4c1aff877614aadf890b2496e0) -->



**SSDT для Visual Studio 2017 (предварительная версия 15.3.0)**

Номер сборки: 14.0.16121.0

**Новые возможности**


Эта предварительная версия — первая версия SSDT для Visual Studio 2017. В этом выпуске появилась поддержка автономной установки с веб-интерфейсом для проектов баз данных SQL Server, Analysis Services, Reporting Services и Integration Services в Visual Studio 2017 15.3 и более поздних версиях.


**Известные проблемы**

- Установщик не локализован.
- Службы SSIS не локализованы.
- Задача запуска пакетов в службах SSIS не поддерживает отладку, если параметр *ExecuteOutofProcess* имеет значение *True*. Эта проблема относится только к отладке. Она не влияет на сохранение, развертывание и запуск с использованием DTExec.exe или каталога SSIS.
- Полный список изменений см. здесь: [журнал изменений--changelog-for-sql-server-data-tools-ssdt.md).
- Сообщить о проблемах можно на сайте [SSDT Connect Feedback](https://connect.microsoft.com/SQLServer/Feedback).
- Для пакетов SSIS, содержащих расширения сторонних разработчиков, невозможно выбирать другие целевые версии сервера.


**SSDT 17.2 для Visual Studio 2015**

Номер сборки: 14.0.61707.300

**Новые возможности**



**Проекты Analysis Services:**
- В диалоговом окне *Роли* теперь можно настроить защиту на уровне объектов, чтобы повысить безопасность табличных моделей с уровнем совместимости 1400.
- Новая возможность выбора пользователей, не имеющих адресов электронной почты, в качестве участников ролей AAD в моделях Analysis Services Azure в проектах SSDT Analysis Services для Visual Studio 2017.
- Новое свойство "Всегда запрашивать" проектов Analysis Services Azure в табличных проектах SSDT Analysis Services, позволяющее настраивать кэширование учетных данных ADAL.


**Исправления ошибок**


**Общие сведения**
- Обновлены ссылки для SQL Server 2017.

**Проекты Analysis Services**
- Внесены исправления для существенного повышения производительности при фиксации изменений, вносимых в меры DAX, и других изменений моделей.
- Исправлен ряд проблем с интеграцией Power Query в проектах Analysis Services, в которых используются табличные модели с уровнем совместимости 1400.
- Исправлена проблема, возникавшая в многомерных проектах в Visual Studio 2017, из-за которой мог происходить сбой загрузки конструктора агрегатных схем.







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Этот раздел содержит похожие статьи, аналогичные недавно измененным, для других предметных областей в том же общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (3+12): документация по **расширенной аналитике для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (5+0): документация по **подключению к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (5+1): документация по **ядру СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (19+82): документация по **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (1+8): документация по **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (12+1): документация по **реляционным базам данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (0+1): документация по **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (7+1): документация по **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (1+1): документация по **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (0+2): документация по **помощнику по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (1+4): документация по **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (4+1): документация по **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (0+1): документация по **средствам для SQL**](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация по **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация по **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)



