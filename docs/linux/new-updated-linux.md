---
title: Обновлено - SQL Server в Linux docs | Документы Microsoft
description: Отображение фрагментов обновленное содержимое для последних измененных в документации Microsoft SQL Server в Linux.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: linux
ms.date: 04/28/2018
ms.openlocfilehash: adc9b9d4dec86f1b0e8807869aa0f20532837cea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Обновление новых и недавно: SQL Server в Linux документы



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2018-02-03** &nbsp; - в - &nbsp; **2018-04-28**
- *Предметной области:* &nbsp; **Microsoft SQL Server в Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Проверка подлинности Active Directory для SQL Server в Linux](sql-server-linux-active-directory-auth-overview.md)
2. [Настройка SQL Server группы доступности AlwaysOn в Windows и Linux (кросс платформенных)](sql-server-linux-availability-group-cross-platform.md)
3. [Всегда работают в группах доступности в Linux](sql-server-linux-availability-group-operate-ha.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Настройка хранилища для установки и обновления SQL Server в Linux](#TitleNum_1)
2. [Настройка SQL Server в Linux с помощью средства mssql conf](#TitleNum_2)
3. [Заметки о выпуске для 2017 г. SQL Server в Linux](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-repositories-for-installing-and-upgrading-sql-server-on-linuxsql-server-linux-change-repomd"></a>1. &nbsp; [Настройка хранилища для установки и обновления SQL Server в Linux](sql-server-linux-change-repo.md)

*Обновлено: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 72.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5ccaa0fcb8895f25c162e4e0494ad4872773de3 29a959be6ee7d58fe0c53e8f91bdd282fb2e6d29  (PR=5676  ,  Filename=sql-server-linux-change-repo.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- Выводит содержимое файла.

```
   sudo cat /etc/yum.repos.d/mssql-server.repo
```

- **Имя** свойство является настроенного репозитория. В таблице в разделе [репозиториев] в этой статье, можно идентифицировать его.

**Удалите старое хранилище (RHEL)**

При необходимости удалите старое хранилище, с помощью следующей команды.

```
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Эта команда предполагает, что файл, указанный в предыдущем разделе была с именем **mssql server.repo**.

**Настройте новый репозиторий (RHEL)**

Настройте новый репозиторий для установки SQL Server и обновления. Используйте одну из следующих команд для настройки репозитория по своему усмотрению.

| Хранилище | Command |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

**<a id="sles"></a> Настройка SLES репозитории**

Выполните следующие действия для настройки на SLES репозиториев.

**Проверьте ранее настроенные репозиториев (SLES)**

Прежде всего проверьте, является ли вы уже зарегистрировали репозитория SQL Server.

- Используйте **zypper сведения** для получения сведений о любой ранее настроенного репозитория.

```
   sudo zypper info mssql-server
```

- **Репозитория** свойство является настроенного репозитория. В таблице в разделе [репозиториев] в этой статье, можно идентифицировать его.

**Удалите старое хранилище (SLES)**

При необходимости удалите старое хранилище. Используйте одну из следующих команд в зависимости от типа ранее настроенного репозитория.

| Хранилище | Команда для удаления |
|---|---|
| **Предварительный просмотр** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>2. &nbsp; [Настройка SQL Server в Linux с помощью средства mssql conf](sql-server-linux-configure-mssql-conf.md)

*Обновлено: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 151.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3664c4d64ea4840dcbc718461ed04403cc486f30 89f708af45ce262057e967e9047f1328e19248ba  (PR=5676  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->




**<a id="masterdatabasedir"></a> Изменить расположение каталога файла базы данных master по умолчанию**


**Filelocation.masterdatafile** и **filelocation.masterlogfile** изменения параметров расположения, где ядра SQL Server ищет файлы базы данных master. По умолчанию это расположение, /var/opt/mssql/data.

Чтобы изменить эти параметры, выполните следующие действия:

- Создайте каталог для новых файлов журнала ошибок. В следующем примере создается новый **/tmp/masterdatabasedir** каталога:

```
   sudo mkdir /tmp/masterdatabasedir
```

- Изменить владельца и группу каталога **mssql** пользователя:

```
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
```

- Используйте для изменения базы данных master каталог по умолчанию для главного файлов данных и журналов с mssql conf **задать** команды:

```
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
```

- Остановите службу SQL Server:

```
   sudo systemctl stop mssql-server
```

- Переместите master.mdf и masterlog.ldf:

```
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
```

- Запустите службу SQL Server:

```
   sudo systemctl start mssql-server
```

> [!NOTE]
> Если SQL Server не удается найти файлы master.mdf и mastlog.ldf в указанном каталоге, будет автоматически создается копия шаблонный системных баз данных в указанном каталоге и SQL Server будет успешно запущен. Однако метаданные, такие как пользовательские базы данных, имен входа на сервер, сертификаты сервера, ключи шифрования, задания агента SQL Server или старый пароль имени входа SA, не обновляются в новую базу данных master. Необходимо будет остановить SQL Server и переместить старые master.mdf и mastlog.ldf на новое место указанного и запустить SQL Server, чтобы продолжить использование существующих метаданных.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>3. &nbsp; [Заметки о выпуске для 2017 г. SQL Server в Linux](sql-server-linux-release-notes.md)

*Обновлено: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2))

<!-- Source markdown line 64.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 367d112a9427bbdd18e0e52cc82264dd169c91ae 63a67be08fa39ece778cf9ca0b9746dd28694574  (PR=5676  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- [Включить агент SQL Server]

**<a id="CU6"></a> CU6 (апрель 2018)**


Это 2017 г. SQL Server выпуска накопительного пакета обновления 6 (CU6). Версия ядра SQL Server для этого выпуска, 14.0.3025.34. Сведения о исправления и улучшения в этом выпуске см. в разделе [ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464).

**Сведения о пакете**


Для установки пакетов вне сети или вручную можно загрузить пакеты RPM и Debian с информацией в таблице ниже:

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.3025.34-3 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[Пакет служб SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) |
| Пакет SLES RPM | 14.0.3025.34-3 | [пакет RPM ядра сервера MSSQL](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) |
| Пакет Debian Ubuntu 16.04 | 14.0.3025.34-3 | [Пакет Debian ядра](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Высокий уровень доступности Debian пакета](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Пакет Debian полнотекстового поиска](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[Пакет служб SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи

- [Новый + обновленные (11 + 6): &nbsp; &nbsp; **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (18 + 0): &nbsp; &nbsp; **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (218 + 14): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (14 + 0): &nbsp; &nbsp; **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (3 + 2): &nbsp; &nbsp; **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (3 + 3): &nbsp; &nbsp; **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (7 + 10): &nbsp; &nbsp; **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (0 + 2): &nbsp; &nbsp; **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (1 + 3): &nbsp; &nbsp; **операций SQL Studio** документы](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новый + обновленные (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (0 + 2): &nbsp; &nbsp; **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)
- [Новый + обновленные (1 + 1): &nbsp; &nbsp; **средства для SQL** документы](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи

- [Новый + обновленные (0 + 0): **Analytics Platform System для SQL** документы](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **PowerShell для SQL** документы](../powershell/new-updated-powershell.md)
- [Новый + обновленные (0 + 0): **образцы для SQL** документы](../samples/new-updated-samples.md)
- [Новый + обновленные (0 + 0): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)

