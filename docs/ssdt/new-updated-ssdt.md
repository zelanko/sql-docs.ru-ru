---
title: "Обновленные документы по SSDT для SQL Server | Документация Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Data Tools (SSDT) для Microsoft SQL Server."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: ssdt
ms.date: 02/03/2018
ms.openlocfilehash: c591ddddd60af31fe2d338fdee25ea2c17ab0ea5
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Новые и недавно обновленные: SQL Server Data Tools (SSDT)



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **03.12.2017**&nbsp;–&nbsp;**03.02.2018**
- *Предметная область:* &nbsp; **SQL Server Data Tools (SSDT)**.




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

1. [Журнал изменений для SQL Server Data Tools (SSDT)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1. &nbsp; [Журнал изменений для SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Обновлено: 18.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 28.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6416949beaee91da2f77dfebb9eb5ed363db4cb7 de18314845cffa197b3fd2ed868f2c330760bedb  (PR=4652  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



**SSDT для Visual Studio 2017 (15.5.1)**

Номер сборки: 14.0.16148.0

**Новые возможности**


Выпуск Visual Studio 2017 (15.5.1) аналогичен версии 15.5.0 за исключением исправления указанных ниже ошибок в установщике.

1.  Устранена ошибка, из-за которой установщик переставал отвечать на запросы после установки служб SQL Server Integration Services.
2.  Устранена ошибка, из-за которой программа установки завершалась сбоем со следующим сообщением: "Требуемая операция для метафайлов не поддерживается (0x800707D3)".

Помимо исправления этих двух ошибок, все приведенные ниже сведения для версии 15.5.0 также относятся к версии 15.5.1.

**SSDT для Visual Studio 2017 (15.5.0)**

Номер сборки: 14.0.16146.0

**Новые возможности**


Средства SSDT для Visual Studio 2017 (15.5.0) прошли этап предварительной версии и предлагаются в виде общедоступной версии.

**Установщик**
1. Локализован пользовательский интерфейс программы установки.
1. Значок заменен на более качественный.

**Integration Services (IS)**
1. В мастере развертывания добавлен этап проверки пакетов при развертывании в среде Azure SSIS IR в ADF. Он позволяет выявить возможные проблемы с совместимостью пакетов SSIS, подлежащих выполнению в Azure SSIS IR. Дополнительные сведения см. в статье [Проверка пакетов SSIS, развертываемых в Azure](..\integration-services\lift-shift\ssis-azure-validate-packages.md).
1. Локализовано расширение служб SSIS.

**Исправления ошибок**


**Integration Services (IS)**
1. Устранена проблема, заключавшаяся в повреждении макета диспетчера подключений OLEDB и ADO.NET.
2. Устранена проблема, из-за которой при попытке изменить задачу обработки измерений возникла ошибка "Сборка не найдена".

**Известные проблемы**


**Integration Services (IS)** Задача запуска пакетов в службах SSIS не поддерживает отладку, если параметр ExecuteOutOfProcess имеет значение True. Эта проблема относится только к отладке. Она не влияет на сохранение, развертывание и запуск с использованием DTExec.exe или каталога SSIS.



**SSDT 17.4 для Visual Studio 2015**

Номер сборки: 14.0.61712.050

**Новые возможности**


**Проекты служб Analysis Services**
- Для табличных проектов добавлено три новых параметра ("Параметры" > "Табличный режим служб Analysis Services" > "Импорт данных").







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
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


