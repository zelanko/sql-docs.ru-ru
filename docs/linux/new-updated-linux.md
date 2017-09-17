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
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 9e6b139e45ccb5184255eabedfb0f809ff64fd2b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Обновление новых и недавно: SQL Server в Linux документы



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон обновлений дат:* &nbsp; **2017 г-07-18** &nbsp; - в - &nbsp; **2017 г-09-11**
- *Предметной области:* &nbsp; **Microsoft SQL Server в Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Следующие ссылки на новые статьи, которые недавно были добавлены.


1. [DB Mail и оповещения по электронной почте с агентом SQL Server в Linux](sql-server-linux-db-mail-sql-agent.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе отображается отрывки обновлений, полученные из статей, в которых были недавно крупных обновлений.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

Compact представлены ссылки на обновленные статьи, которые перечислены в разделе отрывки.

1. [Работы группы доступности высокого уровня ДОСТУПНОСТИ для SQL Server в Linux](#TitleNum_1)
2. [Настройка образов контейнеров 2017 г. SQL Server на Docker](#TitleNum_2)
3. [Настройка SQL Server в Linux с помощью средства mssql conf](#TitleNum_3)
4. [Отзывы пользователей для SQL Server в Linux](#TitleNum_4)
5. [Миграция базы данных SQL Server с Windows и Linux с помощью резервного копирования и восстановления](#TitleNum_5)
6. [Заметки о выпуске для 2017 г. SQL Server в Linux](#TitleNum_6)
7. [Руководство по установке для SQL Server в Linux](#TitleNum_7)
8. [Установка SQL Server Integration Services (SSIS) для Linux](#TitleNum_8)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-operate-ha-availability-group-for-sql-server-on-linuxsql-server-linux-availability-group-failover-hamd"></a>1. &nbsp;[Работать высокой ДОСТУПНОСТИ группы доступности для SQL Server в Linux](sql-server-linux-availability-group-failover-ha.md)

*Обновлено: 2017 г-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 167.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1bef3ece125721b041aa2b9d836329736377df8d 669d2b9a614d680b98280d5b522ba82cf466536c  (PR=2948  ,  Filename=sql-server-linux-availability-group-failover-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



**Обновление группы доступности**


Перед обновлением группы доступности, просмотрите рекомендации по [обновление доступности группы реплики экземпляров--... / database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Следующие разделы описывают выполнить последовательное обновление с экземплярами SQL Server в Linux с группами доступности.

**Этапы обновления в Linux**


Когда реплики доступности группы экземпляров SQL Server в Linux, тип кластера группы доступности — `EXTERNAL` или `NONE`. Группа доступности, которая находится под управлением диспетчера кластеров, помимо отказоустойчивого кластера (WSFC) является `EXTERNAL`. Pacemaker с Corosync примером может служить Диспетчер внешних кластера. Группа доступности с диспетчер кластера не имеет типа кластера `NONE` относятся приведенные ниже действия по обновлению для групп доступности кластера типа `EXTERNAL` или `NONE`.

1. Прежде чем начать, создайте резервную копию каждой базы данных.
2. Обновление экземпляров SQL Server, размещения вторичных реплик.

    а. Сначала обновите асинхронные вторичные реплики.

    б. Обновите синхронные вторичные реплики.

   >[!NOTE]
   >Если группа доступности имеет только асинхронных реплик — Чтобы избежать потери данных измените одной реплики на синхронный и подождите, пока он синхронизирован. Затем обновите этой реплики.

   б.1. Остановить ресурса на узел, содержащий вторичную реплику, предназначенных для обновления

   Перед выполнением команды обновления, остановите ресурс кластера не будет отслеживать ее и выполнять отработку отказа без необходимости. В следующем примере добавляется ограничение расположения на узле, который приведет к ресурса следует остановить. Обновление `ag_cluster-master` с именем ресурса и `nodeName1` с узла, на котором размещена реплика, предназначенных для обновления.

```
   pcs constraint location ag_cluster-master avoids nodeName1
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-2017-container-images-on-dockersql-server-linux-configure-dockermd"></a>2. &nbsp;[Настройка SQL Server 2017 образов контейнеров на Docker](sql-server-linux-configure-docker.md)

*Обновлено: 2017 г-09-05* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 257.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0239ed55a23721eedcc0407a0886d08da47c975b 108fe230151cff7dc91fcdc22218f232394746ec  (PR=3050  ,  Filename=sql-server-linux-configure-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=60272ce672c0a32738b0084ea86f8907ec7fc0a5) -->



1. Определить Docker **тега** для выпуска, который вы хотите использовать. Просмотреть доступные теги [страница концентратора Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. По запросу образ контейнера SQL Server с тегом. Например, для извлечения изображения RC1, замените `<image_tag>` в следующую команду с `rc1`.

```
   docker pull microsoft/mssql-server-linux:<image_tag>
```

1. Чтобы запустить новый контейнер с изображением, укажите имя тега в `docker run` команды. В следующей команде замените `<image_tag>` с версией, требуется запустить.

```
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
```

```
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
```

Эти действия также можно понизить существующий контейнер. Например вы хотите выполнить откат или понизить запущенного контейнера для устранения неполадок или тестирование. Чтобы понизить запущенного контейнера, необходимо использовать метод сохраняемости на папку данных. Выполните те же действия, описанные в [обновить раздел--#upgrade), но указать имя тега для более ранней версии, при запуске нового контейнера.

> [!IMPORTANT]



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>3. &nbsp;[Настройка SQL Server в Linux с помощью средства mssql conf](sql-server-linux-configure-mssql-conf.md)

*Обновлено: 2017 г-09-05* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 233.  ms.author= lbosq.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6117f03e9617b70077488d86f94b32537c4cb9e8 4247a749c056037dd71a27121525be04be6a4f21  (PR=3042  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=46b16dcf147dbd863eec0330e87511b4ced6c4ce) -->



**<a id="localaudit"></a>Каталог локального аудита набора**


**Telemetry.userrequestedlocalauditdirectory** параметр включает локальные аудита и позволяет задать каталог, где локальных журналов аудита на создаются.

1. Создайте целевой каталог для локальных журналов. В следующем примере создается новый **/tmp/аудита** каталога:

```
   sudo mkdir /tmp/audit
```

1. Изменить владельца и группу каталога **mssql** пользователя:

```
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
```

1. Запустите сценарий mssql conf как корень с **задать** для **telemetry.userrequestedlocalauditdirectory**:

```
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
```

1. Перезапустите службу SQL Server:

```
   sudo systemctl restart mssql-server
```

Дополнительные сведения см. в разделе [отзывы по SQL Server на Linux--sql-server-linux-customer-feedback.md.)

**<a id="lcid"></a>Изменение языка SQL Server**


**Language.lcid** изменения параметров языка SQL Server любой поддерживаемым идентификатором языка (LCID).

1. Следующий пример изменяет языковой стандарт на французский (1036):

```
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
```

1. Перезапустите службу SQL Server для применения изменений:

```
   sudo systemctl restart mssql-server
```

**<a id="memorylimit"></a>Задать ограничение памяти**


**Memory.memorylimitmb** настройки элементов управления объем доступной физической памяти (в МБ) для SQL Server. Значение по умолчанию — 80% физической памяти.

1. Запустите сценарий mssql conf как корень с **задать** для **memory.memorylimitmb**. В следующем примере изменяется доступной памяти для SQL Server 3,25 ГБ (3328 МБ).

```
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
```

1. Перезапустите службу SQL Server для применения изменений:



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-customer-feedback-for-sql-server-on-linuxsql-server-linux-customer-feedbackmd"></a>4. &nbsp;[Отзывы для SQL Server в Linux](sql-server-linux-customer-feedback.md)

*Обновлено: 2017 г-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_3) | [Далее](#TitleNum_5))

<!-- Source markdown line 104.  ms.author= anshrest.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9d8122e864804004d91f6b7c5c3d24c4a4114d34 7316ef831c390a854c324f23a02c3fb6005e2fea  (PR=2948  ,  Filename=sql-server-linux-customer-feedback.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->




**Для Docker**

Чтобы включить локальный аудита на docker необходимо иметь Docker [Сохранить ваш data--sql-server-linux-configure-docker.md).

1. Целевой каталог для новых журналов аудита локального будет находиться в контейнере. Создайте целевой каталог для локальных журналов в каталоге узла на компьютере. В следующем примере создается новый **/audit** каталога:

```
   sudo mkdir <host directory>/audit
```


1. Добавить `mssql.conf` файла со строками `[telemetry]` и `userrequestedlocalauditdirectory = <host directory>/audit` в каталоге узла:

```
   echo '[telemetry]' >> <host directory>/mssql.conf
```

```
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
```
2. Запустите образа контейнера
```
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

```
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

**Дальнейшие действия**





&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restoresql-server-linux-migrate-restore-databasemd"></a>5. &nbsp;[Перенос базы данных SQL Server из Windows, Linux с помощью резервного копирования и восстановления](sql-server-linux-migrate-restore-database.md)

*Обновлено: 2017 г-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_4) | [Далее](#TitleNum_6))

<!-- Source markdown line 30.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e78f5516a46eab834f644979d3e1c0ca415fabcd 6b03a01385078290b9f451ac013b628f53e0e8b4  (PR=2948  ,  Filename=sql-server-linux-migrate-restore-database.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



* Компьютер Windows со следующими:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) установлен.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) установлен.
  * Целевой базы данных для миграции.

* Компьютер Linux с установлены следующие компоненты:
  * SQL Server 2017 г., RC2. В разделе примеры использования установки для [RHEL--quickstart-install-connect-red-hat.md) [SLES — краткое руководство install подключения suse.md), или [Ubuntu — краткое руководство install подключения ubuntu.md).
  * SQL Server 2017 г., RC2 [tools--sql-server-linux-setup-tools.md командной строки).

**Создание резервной копии в Windows**


Существует несколько способов создания файла резервной копии базы данных в Windows. В следующих действиях используется SQL Server Management Studio (SSMS).

1. Запуск **SQL Server Management Studio** на компьютере Windows.

1. В диалоговом окне соединения введите **localhost**.

1. В обозревателе объектов разверните **баз данных**.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>6. &nbsp;[Заметки о выпуске для 2017 г. SQL Server в Linux](sql-server-linux-release-notes.md)

*Обновлено: 2017 г-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_5) | [Далее](#TitleNum_7))

<!-- Source markdown line 31.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 4c8b9876f4792782314ba2f9b246405fb8036f84 acb97cf0a2e0bdd039575eaab9c41003316cbb02  (PR=2939  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



**<a id="RC2"></a>Версия-кандидат 2 (август 2017 г.)**


Версия ядра SQL Server для этого выпуска, 14.0.900.75.

**Поддерживаемые платформы**


| Платформа | Файловая система | Руководство по установке |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, рабочей станции, серверов и настольных компьютеров | XFS или EXT4 | [Guide--quickstart-install-connect-red-hat.md установки) |
| Сервер Linux версии 12 SUSE Enterprise с пакетом обновления 2 | EXT4 | [Руководство по установке — краткое руководство install подключения suse.md) |
| Ubuntu 16.04LTS | EXT4 | [Руководство по установке — краткое руководство install подключения ubuntu.md) |
| Подсистема docker 1.8 + в Windows, Mac или Linux | Недоступно | [Руководство по установке — краткое руководство install подключения docker.md) |

> [!NOTE]
> Необходимо по крайней мере 3,25 ГБ памяти для запуска SQL Server в Linux.
> Модуль SQL Server был протестирован 1,5 ТБ памяти в данный момент.

**Сведения о пакете**


Сведения о пакете и адреса для пакеты RPM и Debian, перечислены в следующей таблице. Обратите внимание, что не требуется непосредственно загрузить эти пакеты при использовании действия в следующих руководствах по установке:

- [Установка пакета SQL Server — sql server-linux setup.md)
- [Установка package--sql-server-linux-setup-full-text-search.md Full-text Search)
- [Установка package--sql-server-linux-setup-sql-agent.md агента SQL Server)

| Пакет | версия пакета | Файлы для загрузки |
|-----|-----|-----|
| Пакет Red Hat RPM | 14.0.900.75-1 | [Пакет RPM ядра](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[Высокий уровень доступности RPM пакета](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[Пакет полнотекстового поиска об/мин](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[Пакет RPM агента SQL Server](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) |



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-installation-guidance-for-sql-server-on-linuxsql-server-linux-setupmd"></a>7. &nbsp;[Руководство по установке для SQL Server в Linux](sql-server-linux-setup.md)

*Обновлено: 2017 г-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_6) | [Далее](#TitleNum_8))

<!-- Source markdown line 70.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 00394e1733568a55243788d828968ff9b58a3c99 8ba2bf6f9cf4b5f54a6ee0f4d16d4437d5724880  (PR=2971  ,  Filename=sql-server-linux-setup.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=303d3b74da3fe370d19b7602c0e11e67b63191e7) -->



**<a id="rollback"></a>Откат SQL Server**


Для отката или возврат к предыдущей версии SQL Server в предыдущем выпуске выполните следующие действия:

1. Укажите номер версии для пакета SQL Server, который вы хотите перейти на. Список номеров пакета см. в разделе [notes--sql-server-linux-release-notes.md выпуск.)

1. Перейти к предыдущей версии SQL Server. В приведенных ниже команд, замените `<version_number>` с номером версии SQL Server, определенный на шаге 1.

   | Платформа | Выполнение команд пакета обновления |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> Она поддерживается только может понижаться до выпуска в пределах той же основной версии, например 2017 г. SQL Server.

> [!IMPORTANT]
> Возврат к предыдущей версии поддерживаются только между RC2 и версии-кандидата 1 в данный момент.




&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-install-sql-server-integration-services-ssis-on-linuxsql-server-linux-setup-ssismd"></a>8. &nbsp;[Установке SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)

*Обновлено: 2017 г-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_7))

<!-- Source markdown line 66.  ms.author= lle.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a3fecd2553d1b25406445b8a26b22c9015dd98fe f836d560513fef1217e7dbce0ab85f78eec6f937  (PR=2948  ,  Filename=sql-server-linux-setup-ssis.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



Если у вас уже есть `mssql-server-is` установлены, можно обновить до последней версии с помощью следующей команды:

```
sudo apt-get install mssql-server-is
```


Чтобы удалить `mssql-server-is`, можно запустить следующую команду:
```
sudo apt-get remove msssql-server-is
```



**<a name="RHEL"></a>Установка служб SSIS на RHEL**

Чтобы установить `mssql-server-is` пакет в RHEL, выполните следующие действия:


1.  Перейдите в режим суперпользователя.

```
    sudo su
```


2.  Загрузите файл конфигурации Microsoft SQL Server Red Hat репозитория.

```
    curl https://packages.microsoft.com/config/rhel/7/mssql-server.repo > /etc/yum.repos.d/mssql-server.repo
```


3.  Выход из режима суперпользователя.

```
    exit
```


4.  Выполните следующие команды для установки SQL Server Integration Services.

```
    sudo yum install -y mssql-server-is
```


5.  После установки, выполните команду `ssis-conf`.







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



