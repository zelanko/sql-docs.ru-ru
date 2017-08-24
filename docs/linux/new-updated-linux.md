---
title: "Обновлено - SQL Server в Linux docs | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации Microsoft SQL Server в Linux."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: rothja
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: linux-sql
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 13c237af359c543f6a99a0fce101af81b5eb2bcf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Обновление новых и недавно: SQL Server в Linux документы

Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2017 г-05-23** &nbsp; - в - &nbsp; **2017 г-07-17**
- *Предметной области:* &nbsp; **Microsoft SQL Server в Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые были добавлены недавно.


1. [Запускать образ контейнера 2017 г. SQL Server с помощью Docker](quickstart-install-connect-docker.md)
2. [Установка SQL Server и создать базу данных в Red Hat](quickstart-install-connect-red-hat.md)
3. [Установка SQL Server и создать базу данных на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
4. [Установка SQL Server и создать базу данных на Ubuntu](quickstart-install-connect-ubuntu.md)
5. [Пример: Автоматической установки SQL Server сценария установки для Red Hat Enterprise Linux](sample-unattended-install-redhat.md)
6. [Пример: Сценария установки автоматической установки SQL Server для SUSE Linux Enterprise Server](sample-unattended-install-suse.md)
7. [Пример: Сценарий установки автоматической установки SQL Server для Ubuntu](sample-unattended-install-ubuntu.md)
8. [Проверка подлинности Active Directory с SQL Server в Linux](sql-server-linux-active-directory-authentication.md)
9. [Высокий уровень доступности и защиты данных в конфигурации группы доступности](sql-server-linux-availability-group-ha.md)
10. [Настройка образов контейнеров 2017 г. SQL Server на Docker](sql-server-linux-configure-docker.md)
11. [Отзывы пользователей для SQL Server в Linux](sql-server-linux-customer-feedback.md)
12. [Шифрование соединений с SQL Server в Linux](sql-server-linux-encrypted-connections.md)
13. [Установка SQL Server Integration Services (SSIS) для Linux](sql-server-linux-setup-ssis.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

Compact представлены ссылки на обновленные статьи, перечисленные в разделе отрывки.



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе отображается отрывки обновлений, полученные из статей, в которых были недавно крупных обновлений.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-sles-cluster-for-sql-server-availability-groupsql-server-linux-availability-group-cluster-slesmd"></a>1. &nbsp;[Настройка SLES кластера для группы доступности SQL Server](sql-server-linux-availability-group-cluster-sles.md)

*Updated: 2017-06-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 189.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f8d28af253be1dc67615f1ea04135b2f6dff3b71 8be07deddcf0c348d75bf5b4f44615c2383e0722  (PR=2150  ,  Filename=sql-server-linux-availability-group-cluster-sles.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=6dccaff93a6c8b2374a1fad069b2f597898802fc) -->



**Значение свойства кластера start сбой является Неустранимая false**


`Start-failure-is-fatal`Указывает ли сбой запуска ресурса на узле предотвращает последующие попытки запуска на этом узле. Если задано значение `false`, кластер решить, следует ли попробуйте запустить на том же узле, еще раз на основании ресурса текущего счетчика и миграции Порог сбоя. Таким образом после перехода на другой ресурс, Pacemaker повторит попытку начиная ресурс группы доступности на первый основной после экземпляра SQL Server. Pacemaker берет на себя при понижении роли реплики во вторичные и он автоматически будет повторно подключиться к группе доступности. Кроме того Если `start-failure-is-fatal` равно `false`, кластере вернется к настроенным failcount ограничения, настроенного с пороговым значением миграции, поэтому необходимо убедиться, что по умолчанию для порога миграции обновляется соответствующим образом.

Чтобы обновить значение свойства false выполнять:
```
sudo crm configure property start-failure-is-fatal=false
sudo crm configure rsc_defaults migration-threshold=5000
```
Если свойство имеет значение по умолчанию `true`, если первая попытка запустить ресурс, вмешательства пользователя после автоматического перехода на количество сбоев ресурсов очистки и сброса конфигурации с помощью: `sudo crm resource cleanup <resourceName>` команды.

Дополнительные сведения о Pacemaker свойства кластера см. в разделе [Настройка ресурсов кластера](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html).

**Настройка разграничения (STONITH)**

Pacemaker кластера поставщиков требуют STONITH должно быть включено и разграничения устройству, настроенному для поддерживаемых кластера. Если диспетчер ресурсов кластера не удается определить состояние узла или ресурса на узле, разграничения позволяет снова подключить известного состояния кластера.
Ресурс уровня разграничения главным образом, гарантируется без повреждения данных в случае сбоя путем настройки ресурса. Можно использовать разграничения уровня ресурсов, например, с DRBD (распределенных реплицируются блоков) для пометки диска на узле как устаревший, когда канал связи выходит из строя.




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>2. &nbsp;[Заметки о выпуске для 2017 г. SQL Server в Linux](sql-server-linux-release-notes.md)

*Updated: 2017-06-20* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 156.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 684da20f7834000886d7a93f83563c55dc3cf9a6 8597bcde7e5754bb7f38de1ec980027245dac6e5  (PR=2115  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=424a23fd98876db808b91f017e7acbcb5b4daa45) -->



**Службы SQL Server Integration Services**

Может запускать пакеты служб SSIS в Linux. Дополнительные сведения см. в разделе [блога post Представляем поддержку SSIS для Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/). Учтите следующие известные проблемы в этом выпуске.

- **Mssql сервер является** пакета поддерживаются только для Ubuntu на данный момент.

- Следующие функции не поддерживаются при выполнении пакетов служб SSIS в Linux:
  - Базы данных каталога служб SSIS
  - Планирование выполнения пакетов агентом SQL
  - Проверка подлинности Windows.
  - Компоненты сторонних разработчиков
  - Драйверов ODBC
  - Диспетчер соединений ODBC, источника и назначения (поддерживается с помощью служб SSIS при обновлении 2.1 Linux CTP-версия)
  - Система отслеживания измененных данных (CDC)
  - Масштабирование
  - Пакет дополнительных компонентов Azure
  - Поддержка Hadoop и HDFS
  - Соединитель Microsoft Connector для SAP BW

С помощью служб SSIS на Linux CTP-версии 2.1 обновления пакетов служб SSIS можно использовать подключения ODBC в Linux. Дополнительные сведения см. в разделе [записи блога Представляем поддержка ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Аналогичные статей

В этом разделе перечислены схожий статей для недавно обновлены статьи в других предметных областей, в одном репозитории GitHub.com: [MicrosoftDocs /**sql документы pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметных областей, которые имеют новые или недавно обновленные статьи

- [Новый + обновленные (4 + 4): **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (2 + 0): **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (1 + 2): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (6 + 0): **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (13 + 2): **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (1 + 0): **Master Data Services (MDS) для SQL** документы](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (1 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (8 + 4): **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (2 + 2): **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (0 + 1): **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (1 + 0): **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)
- [Новый + обновленные (1 + 0): **средства для SQL** документы](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметных областей, в которых нет новых или недавно обновленных статей

- [Новый + обновленные (0 + 0): **объектов данных ActiveX (ADO) для SQL** документы](../ado/new-updated-ado.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новый + обновленные (0 + 0): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **PowerShell для SQL** документы](../powershell/new-updated-powershell.md)
- [Новый + обновленные (0 + 0): **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../sample/new-updated-sample.md)
- [Новый + обновленные (0 + 0): **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)


&nbsp;


