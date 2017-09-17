---
title: "Обновлено - SSMA для документации по SQL Server | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации для SQL Server Migration Assistant (SSMA) для Microsoft SQL Server."
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
ms.workload: ssma-sql-server-migration-assistant
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 68df82bc7da6d7ef5aed3522c06704fb92bb0982
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-migration-assistant-ssma"></a>Новые и недавно обновленные: SQL Server Migration Assistant (SSMA)



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон обновлений дат:* &nbsp; **2017 г-07-18** &nbsp; - в - &nbsp; **2017 г-09-11**
- *Предметной области:* &nbsp; **SQL Server Migration Assistant**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Следующие ссылки на новые статьи, которые недавно были добавлены.


***На данный момент новых статей нет.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе отображается отрывки обновлений, полученные из статей, в которых были недавно крупных обновлений.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

Compact представлены ссылки на обновленные статьи, которые перечислены в разделе отрывки.

1. [Какой &#39; новые возможности SSMA для DB2 (DB2ToSQL)](#TitleNum_1)
2. [Помощник по миграции SQL Server](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-what39s-new-in-ssma-for-db2-db2tosqldb2what-s-new-in-ssma-for-db2-db2tosqlmd"></a>1. &nbsp;[Что &#39; новые возможности SSMA для DB2 (DB2ToSQL)](db2/what-s-new-in-ssma-for-db2-db2tosql.md)

*Обновлено: 2017 г-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 24.  ms.author= "Shamikg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c5dfb378ac578f54935a8a1fa7194398f3631017 f4427d1857894ad348cef5c92fbf6b51d00ee652  (PR=3070  ,  Filename=what-s-new-in-ssma-for-db2-db2tosql.md  ,  Dirpath=docs\ssma\db2\  ,  MergeCommitSha40=0b832a9306244210e693bde7c476269455e9b6d8) -->



**SSMA v7.4**

V7.4 выпуск SSMA для DB2 содержит следующие изменения:
- **Время ожидания запроса** теперь доступен при обнаружении объекта схемы в исходной и целевой.
! [параметр времени ожидания запроса —... /Media/Query-timeout_red.PNG)

- Метрика качества и преобразование усовершенствованы целевой исправления, на основе отзывов клиентов.

> [!IMPORTANT]
> Версия .net 4.5.2 является необходимым условием для установки SSMA v7.4. Кроме того начиная с v7.4, 32-разрядной версии SSMA прекращается.

**SSMA v7.3**

V7.3 выпуск SSMA для DB2 содержит следующие изменения:
- Улучшенное качество и преобразование метрику с целевой исправления на основе отзывов клиентов.
- SSMA расширения среды .NET framework, представляемый через следующие элементы:
  - Экспорт функций в проект SQL Server Data Tools (SSDT).
    -   Теперь можно экспортировать скриптов схемы с SSMA для проекта SSDT. Скрипты схемы можно использовать для внесения изменений дополнительные схемы и развертывания базы данных.
! [Сохранить как команда проекта SSDT--... /Media/Export-Schema-scripts_red.PNG)
  - Библиотеки, которые могут быть использованы SSMA для выполнения пользовательских преобразований.
    - Теперь можно создать код, который может обработать синтаксис пользовательского преобразования и преобразования, которые не были обработаны ранее SSMA.
      - Инструкции о том, как создать пользовательский преобразователь доступны в этой записи блога [расширение SQL Server Migration Assistant по возможности конвертации](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Пример проекта для преобразования можно загрузить это [блога](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

**SSMA v7.2**

V7.2 выпуск SSMA для DB2 содержит следующие изменения:
- Улучшенное качество и преобразование метрику с целевой исправления на основе отзывов клиентов.
- Улучшения телеметрии для предоставления более точек данных для устранения проблем клиентов и повысить скорость преобразования элемента SSMA.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-migration-assistantsql-server-migration-assistantmd"></a>2. &nbsp;[SQL Server Migration Assistant](sql-server-migration-assistant.md)

*Обновлено: 2017 г-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1))

<!-- Source markdown line 36.  ms.author= "Shamikg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 340d718e85fa73c6722862a0a7ba90239b247389 b29f4be2b6d208fd6038c2f9e1c7f0b7bd6b9ed7  (PR=3070  ,  Filename=sql-server-migration-assistant.md  ,  Dirpath=docs\ssma\  ,  MergeCommitSha40=0b832a9306244210e693bde7c476269455e9b6d8) -->



**Поддерживаемые источники и целевой версии**

Для поддерживаемых источников данных ознакомьтесь с информацией в центре загрузки для загрузки SSMA.

SSMA поддержка следующих версий.

- SQL Server 2008
- SQL Server 2008 R2
- SQL Server 2012
- SQL Server 2014
- SQL Server 2016
- База данных SQL Azure
- SQL Server 2017 г. в Windows и Linux (Предварительная версия)
- ** Хранилище данных azure SQL

** Этот целевой объект поддерживается только SSMA для Oracle.









## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

В этом разделе перечислены схожий статей для недавно обновлены статьи в других предметных областей, в общедоступный репозиторий GitHub.com: [MicrosoftDocs, sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новый + обновленные (3 + 12): **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (5 + 0): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (5 + 1): **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (19 + 82): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (1 + 8): **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (12 + 1): **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (0 + 1): **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (7 + 1): **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (1 + 1): **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (0 + 2): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новый + обновленные (1 + 4): **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (4 + 1): **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)
- [Новый + обновленные (0 + 1): **средства для SQL** документы](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новый + обновленные (0 + 0): **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новый + обновленные (0 + 0): **Master Data Services (MDS) для SQL** документы](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)



