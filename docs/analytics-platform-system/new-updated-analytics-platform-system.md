---
title: Обновлено - система платформы аналитики docs | Документы Microsoft
description: Отображение фрагментов обновленное содержимое для последних измененных в документации, Analytics Platform System для Microsoft SQL Server.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 94b7666476874e610991ebf838ad259f3d0bb85a
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="new-and-recently-updated-analytics-platform-system-for-sql-server"></a>Новые и недавно обновленные: система платформы аналитики для SQL Server

Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон дат обновлений:* &nbsp; **03.12.2017**&nbsp;–&nbsp;**03.02.2018**
- *Предметной области:* &nbsp; **Analytics Platform System для SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


***Сейчас новые статьи отсутствуют.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Настройка подключения к PolyBase для внешних данных](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-polybase-connectivity-to-external-dataconfigure-polybase-connectivity-to-external-datamd"></a>1. &nbsp; [Настройка подключения к PolyBase для внешних данных](configure-polybase-connectivity-to-external-data.md)

*Обновлено: 29.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 132.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 947f789480da66b9f636f39b30caec6be60d8c4d d4d4d45fbbb8e10ed6f26fe12f9a25d2e8e4f068  (PR=4741  ,  Filename=configure-polybase-connectivity-to-external-data.md  ,  Dirpath=docs\analytics-platform-system\  ,  MergeCommitSha40=0a44ce9993ebf61f86e409255a1d58d47993951a) -->



**Конфигурация Kerberos**

Обратите внимание, что при PolyBase проходит проверку подлинности Kerberos защищенного кластера, параметр hadoop.rpc.protection должно быть присвоено проверки подлинности. При этом обмен данными между узлами Hadoop остается в незашифрованном виде.

 Для подключения к защищенным с помощью Kerberos кластеру [с помощью MIT KDC]:


1.  Найдите каталог конфигурации Hadoop в каталоге установки на узле управления:

    ```
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```

2.  Найдите значение конфигурации для ключей конфигурации, перечисленных в таблице, на компьютере с Hadoop. (Найдите файлы в каталоге конфигурации Hadoop на этом же компьютере.)

3.  Скопируйте значения конфигурации в свойство value соответствующих файлов на узел элемента управления.

    |**#**|**Файл конфигурации**|**Ключ конфигурации**|**Действие**|
    |------------|----------------|---------------------|----------|
    |1|core-site.xml|polybase.kerberos.kdchost|Укажите имя узла KDC. Например, kerberos.your-realm.com|
    |2|core-site.xml|polybase.kerberos.realm|Укажите область Kerberos. Например, YOUR-REALM.COM|
    |3|core-site.xml|hadoop.security.authentication|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, KERBEROS<br></br>**Примечание о безопасности:** слово KERBEROS должно быть написано прописными буквами. При использовании строчных букв функция может не включиться.|
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: hdfs/_HOST@YOUR-REALM.COM.|
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: mapred/_HOST@YOUR-REALM.COM.|
    |6|mapred-site.xml|mapreduce.jobhistory.address|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, 10.193.26.174:10020|
    |7|yarn-site.xml yarn|yarn.resourcemanager.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: yarn/_HOST@YOUR-REALM.COM|







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
- [Новый + обновленные (0 + 0): **объектов данных ActiveX (ADO) для SQL** документы](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../samples/new-updated-samples.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)


