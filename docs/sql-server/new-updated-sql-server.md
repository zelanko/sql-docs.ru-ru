---
title: Обновленные документы по SQL Server | Документация Майкрософт
description: Отрывки из недавно обновленного содержимого в документации по SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: 3575f65c751d91e2a32cf0acbf76665b42378d6a
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084436"
---
# <a name="new-and-recently-updated-sql-server-docs"></a>Новые и недавно обновленные документы для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Даты обновлений:* &nbsp; **02.03.2018**&nbsp;–&nbsp;**28.04.2018**
- *Предметная область:* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Участие в работе над документацией по SQL Server](sql-server-docs-contribute.md)
2. [Приложение о конфиденциальности в SQL Server](sql-server-privacy.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Заметки о выпуске пакетов обновления к SQL Server 2012](#TitleNum_1)
2. [Заметки о выпуске SQL Server 2016](#TitleNum_2)
3. [Документация по SQL Server](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2012-service-pack-release-notessql-server-2012-sp4-release-notesmd"></a>1. &nbsp; [Заметки о выпуске пакетов обновления для SQL Server 2012](sql-server-2012-sp4-release-notes.md)

*Обновление: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 57.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ce108992ea942b4a11f30d67a1a52d7f26868caa a6269ba2cb2d3b3b54aebf5087dc4d513e476a96  (PR=5676  ,  Filename=sql-server-2012-sp4-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- **Автоматическое секционирование soft-NUMA**. В SQL 2014 с пакетом обновления 2 (SP2) при включении флага трассировки 8079 на уровне сервера секционирование [Soft-NUMA](https://msdn.microsoft.com/library/ms345357(SQL.120).aspx) реализуется автоматически. Если флаг трассировки 8079 включен во время запуска, SQL Server 2014 с пакетом обновления 2 (SP2) опрашивает структуру оборудования и автоматически настраивает soft-NUMA на системах, сообщивших о наличии о восьми или более ЦП на узел NUMA. Автоматическая реализация soft-NUMA учитывает многопоточность (потоки/логические процессоры). Секционирование и создание дополнительных узлов позволяет масштабировать фоновую обработку за счет увеличения числа прослушивателей и масштаба вычислений, а также расширения возможностей сети и шифрования. Рекомендуется использовать автоматическое секционирование soft-NUMA для предварительного тестирования производительности рабочих нагрузок перед их активацией в рабочей среде.

**Заметки о выпуске пакета обновления 3**


**Страницы скачивания**

- [Пакет дополнительных компонентов SQL Server 2012 с пакетом обновления 3 (SP3)](http://go.microsoft.com/fwlink/?linkid=615935)
- [SQL Server 2012 Express с пакетом обновления 3 (SP3)](http://go.microsoft.com/fwlink/?linkid=692144)

Дополнительные сведения об определении расположении и имени файла для скачивания в зависимости от установленной у вас версии программы см. в разделе "Выбор подходящего файла для скачивания" статьи [Информация о выпуске SQL Server 2012 с пакетом обновления 3](https://support.microsoft.com/help/3072779/sql-server-2012-service-pack-3-release-information).

**Заметки о выпуске пакета обновления 2**


**Страницы скачивания**

- [Пакет дополнительных компонентов SQL Server 2012 с пакетом обновления 2 (SP2)](http://go.microsoft.com/fwlink/?LinkID=401008)
- [SQL Server 2012 Express с пакетом обновлений 2 (SP2)](http://go.microsoft.com/fwlink/?LinkID=401007)

Используйте таблицу, приведенную ниже, для определения расположения и имени файла для загрузки, основанные на вашей текущей установленной версии. Страницы загрузки содержат требования к системе и основные инструкции по установке.

|Если сейчас установлена версия...|И вы хотите...|Скачайте и установите...|



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-2016-release-notessql-server-2016-release-notesmd"></a>2. &nbsp; [Заметки о выпуске SQL Server 2016](sql-server-2016-release-notes.md)

*Обновлено: 27.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 25.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a15210866acf524dae49f3a7fd7957c9ffa6a78a 7257cb2017779242cbb8fa2b562f4b102502e942  (PR=5695  ,  Filename=sql-server-2016-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=d1c114b98fea55d2d4829dffdb25daf1b3f73dc2) -->



  В этой статье описываются ограничения и проблемы, связанные с выпусками SQL Server 2016, включая пакеты обновления. Сведения о новых возможностях см. в разделе [Что нового в SQL Server 2016](https://docs.microsoft.com/sql/sql-server/what-s-new-in-sql-server-2016).

- Скачайте SQL Server 2016 в **[Центре оценки](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**.
- Маленький значок виртуальной машины Azure: у вас есть учетная запись Azure?  Тогда перейдите **[сюда](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** , чтобы запустить виртуальную машину с уже установленным SQL Server 2016 с пакетом обновления 1 (SP1).
- Скачайте SSMS. Чтобы получить последнюю версию среды SQL Server Management Studio, перейдите на страницу **[Скачивание SQL Server Management Studio (SSMS)]**.

**<a name="bkmk_2016sp2"></a>SQL Server 2016 с пакетом обновления 2 (SP2)**


SQL Server 2016 с пакетом обновления 2 (SP2) включает все накопительные обновления, выпущенные после версии 2016 с пакетом обновления 1 (SP1), вплоть до накопительного пакета обновления 8 включительно.

- [Центр загрузки Майкрософт: SQL Server 2016 с пакетом обновления 2 (SP2)](https://go.microsoft.com/fwlink/?linkid=869608)
- Полный список обновлений см. в разделе [Сведения о выпуске SQL Server 2016 с пакетом обновления 2 (SP2)](https://support.microsoft.com/help/4052908/sql-server-2016-service-pack-2-release-information)



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sql-server-documentationsql-server-technical-documentationmd"></a>3. &nbsp; [Документация по SQL Server](sql-server-technical-documentation.md)

*Обновлено: 27.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_2))

<!-- Source markdown line 77.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0262010ba39785a6d46b42f8469fb17701f13008 c69a83236391d039381a93c65ebbb2efa53e11b8  (PR=5695  ,  Filename=sql-server-technical-documentation.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=d1c114b98fea55d2d4829dffdb25daf1b3f73dc2) -->




<!-- : : : m-r -->
**Попробуйте SQL Server!**
- Скачать из Evaluation Center: [скачать SQL Server для Windows](http://go.microsoft.com/fwlink/?LinkID=829477)
- Скачать из Evaluation Center: скачать SQL Server Management Studio (SSMS)
- Скачать из Evaluation Center: скачать SQL Server Data Tools (SSDT)
- Создать виртуальную машину: [развернуть виртуальную машину с SQL Server](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)





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

