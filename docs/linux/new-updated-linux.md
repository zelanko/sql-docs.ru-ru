---
title: "Обновлено - SQL Server в Linux docs | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации Microsoft SQL Server в Linux."
services: na
documentationcenter: 
author: MightyPen
manager: craigg
editor: rothja
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: linux-sql
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: d477af0c4c7027892d4ade8e586c9a9b908a05ea
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Обновление новых и недавно: SQL Server в Linux документы



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон дат обновлений:* &nbsp; **28.09.2017**&nbsp;–&nbsp;**02.12.2017**
- *Предметной области:* &nbsp; **Microsoft SQL Server в Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные новые статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Запустите 2017 г. SQL Server в облаке](quickstart-install-connect-clouds.md)
2. [Изменить репозиториев из репозитория предварительного просмотра в репозитории общедоступной версии](sql-server-linux-change-repo.md)
3. [Рекомендации по производительности и рекомендации по конфигурации для 2017 г. SQL Server в Linux](sql-server-linux-performance-best-practices.md)
4. [Экземпляры отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-concepts.md)
5. [Настройка экземпляра отказоустойчивого кластера — iSCSI - SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
6. [Настроить экземпляр отказоустойчивого кластера — NFS - SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
7. [Настройте экземпляр отказоустойчивого кластера — SMB - SQL Server в Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)
8. [Работать экземпляр отказоустойчивого кластера — SQL Server в Linux](sql-server-linux-shared-disk-cluster-operate.md)
9. [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
10. [Восстановление базы данных SQL Server в контейнер Linux Docker](tutorial-restore-backup-in-sql-server-container.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Запускать образ контейнера 2017 г. SQL Server с помощью Docker](#TitleNum_1)
2. [Настройка группы доступности AlwaysOn для SQL Server в Linux](#TitleNum_2)
3. [Высокий уровень доступности и защиты данных в конфигурации группы доступности](#TitleNum_3)
4. [Настройка образов контейнеров 2017 г. SQL Server на Docker](#TitleNum_4)
5. [Шифрование соединений с SQL Server в Linux](#TitleNum_5)
6. [Создание и запуск задания агента SQL Server в Linux](#TitleNum_6)
7. [Руководство по установке для SQL Server в Linux](#TitleNum_7)
8. [Настроить экземпляр отказоустойчивого кластера — SQL Server для Linux (RHEL)](#TitleNum_8)
9. [Устранение неполадок SQL Server в Linux](#TitleNum_9)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-run-the-sql-server-2017-container-image-with-dockerquickstart-install-connect-dockermd"></a>1. &nbsp;[Запускать образ контейнера 2017 г. SQL Server с помощью Docker](quickstart-install-connect-docker.md)

*Обновление: 30.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 261.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2aaf953c2f1fb675b1304186108fbef1eebf6f8f f7cd42bb320a8892a5ec63ce999186438097636a  (PR=4150  ,  Filename=quickstart-install-connect-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



**Удаление контейнера**


Если вы хотите удалить контейнер SQL Server, используемые в этом учебнике, выполните следующие команды:

```
sudo docker stop sql1
sudo docker rm sql1
```

```
docker stop sql1
docker rm sql1
```

> [!WARNING]
> Остановка и удаление контейнера окончательно удаляет все данные SQL Server в контейнере. Если необходимо сохранить данные, [создайте и скопируйте файл резервной копии из container--tutorial-restore-backup-in-sql-server-container.md) или используйте [контейнер данных сохраняемости technique--sql-server-linux-configure-docker.md#persist).




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-always-on-availability-group-for-sql-server-on-linuxsql-server-linux-availability-group-configure-hamd"></a>2. &nbsp;[Настройка группы доступности AlwaysOn для SQL Server в Linux](sql-server-linux-availability-group-configure-ha.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 129.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3c7e6bc862e5b062a855918efbeee5fe748b7236 6900c9a30ce04ce54e7aaa270ef7d276c18f9afd  (PR=4150  ,  Filename=sql-server-linux-availability-group-configure-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



- Создание группы доступности с двумя синхронными репликами и конфигурации реплики.

   >[!IMPORTANT]
   >Такая архитектура позволяет любого выпуска SQL Server для размещения третья реплика. Например третья реплика может размещаться на SQL Server Enterprise Edition. В выпуске Enterprise Edition является тип конечной точки только допустимые `WITNESS`.

```sql
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
       N'**<node1>**' WITH (
          ENDPOINT_URL = N'tcp://**<node1>**:**<5022>**',
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
          FAILOVER_MODE = EXTERNAL,
          SEEDING_MODE = AUTOMATIC
          ),
       N'**<node2>**' WITH (
          ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**',
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
          FAILOVER_MODE = EXTERNAL,
          SEEDING_MODE = AUTOMATIC
          ),
       N'**<node3>**' WITH (
          ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**',
          AVAILABILITY_MODE = CONFIGURATION_ONLY
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-high-availability-and-data-protection-for-availability-group-configurationssql-server-linux-availability-group-hamd"></a>3. &nbsp;[Высокого уровня доступности и защиты данных в конфигурации группы доступности](sql-server-linux-availability-group-ha.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 106.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e6bee794ce19f1ed62298b4a0cce7207550f1595 b64726cd6e91721850721786d26c170d59fc320a  (PR=4150  ,  Filename=sql-server-linux-availability-group-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Значение по умолчанию для `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` равно 0. В следующей таблице описывается поведение доступности.

| |Высокий уровень доступности & </br> Защита данных | Защита данных
|:---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>*</sup>|1
|Сбой первичной реплики | Автоматический переход на другой ресурс. R — новый первичный / W. | Автоматический переход на другой ресурс. Новый сервер-источник недоступен для пользовательских транзакций.
|Вторичная реплика сбоя | Первичный — для чтения и записи, работой в незащищенном режиме к потере данных (если основной завершается ошибкой и не может быть восстановлена). Без автоматического перехода на другой ресурс при сбое основной, а также. | Основной доступен не для пользовательских транзакций. Ни одна из реплик на переход к, если первичная невозможна.
|Только реплики простой конфигурации | Основной R / W. Без автоматического перехода на другой ресурс при сбое основной, а также. | Основной R / W. Без автоматического перехода на другой ресурс при сбое основной, а также.
|Синхронного сервера-получателя + конфигурации только для отключения реплики| Основной доступен не для пользовательских транзакций. Автоматическая отработка отказа. | Основной доступен не для пользовательских транзакций. Переход на другой ресурс, если ни одна из реплик также основной завершается ошибкой.
<sup>*</sup>По умолчанию

>[!NOTE]
>Экземпляр SQL Server, на котором размещена реплика только конфигурации может также содержать другие базы данных. Он также может выступать только базу данных конфигурации для более чем одной группы доступности.

**Требования**


* Все реплики в группу доступности с репликами только конфигурации должен быть SQL Server 2017 г накопительным пакетом обновления 1 или более поздней версии.
* Любой выпуск SQL Server может размещать реплику только конфигурации, включая SQL Server Express.
* Группа доступности должна по крайней мере одна вторичная реплика - дополнение к первичной реплике.
* Максимальное число реплик на один экземпляр SQL Server не считаются конфигурации реплики. SQL Server standard edition поддерживает до трех реплик, SQL Server Enterprise Edition позволяет до 9.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-configure-sql-server-2017-container-images-on-dockersql-server-linux-configure-dockermd"></a>4. &nbsp;[Настройка SQL Server 2017 образов контейнеров на Docker](sql-server-linux-configure-docker.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_3) | [Далее](#TitleNum_5))

<!-- Source markdown line 34.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c759fb88ae8d654414202f28c5fc58dfd02581bf fd270118f2f4608fceaf563fc143951b41097bdb  (PR=4150  ,  Filename=sql-server-linux-configure-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Этот раздел конфигурации содержит сценарии использования дополнительных в следующих разделах.

**<a id="production"></a>Запустите производственного образы контейнеров**


Краткое руководство, в предыдущем разделе выполняется бесплатный выпуск SQL Server Developer из Docker Hub. Большая часть информации по-прежнему применяется в том случае, если вы хотите запустить производства образы контейнеров, таких как выпуски Enterprise, Standard или Web. Однако существуют некоторые различия, которые здесь описаны.

- SQL Server можно использовать в производственной среде, только если у вас есть действительная лицензия. Можно получить бесплатную лицензию SQL Server Express рабочей [здесь](https://go.microsoft.com/fwlink/?linkid=857693). Лицензии SQL Server Standard и Enterprise Edition доступны через [корпоративного лицензирования Майкрософт](https://www.microsoft.com/Licensing/licensing-programs/licensing-programs.aspx).

- Образы контейнеров рабочей среде SQL Server должны извлекаться с [Docker хранилище](https://store.docker.com). Если вы уже нет, создайте учетную запись в хранилище Docker.

- Образ контейнера разработчика в магазине Docker можно настроить для запуска в выпусках производства. Для запуска рабочей версии, выполните следующие действия:

   1. Во-первых Войдите на свой идентификатор docker из командной строки.

```
      docker login
```

   1. Далее необходимо для получения бесплатной разработчик образ контейнера в хранилище Docker. Последовательно выберите пункты [https://store.docker.com/images/mssql-server-linux](https://store.docker.com/images/mssql-server-linux), нажмите кнопку **продолжить извлечение**и следуйте инструкциям.

   1. Ознакомьтесь с требованиями и выполнить процедуры из раздела [примеры использования — краткое руководство install подключения docker.md). Однако имеются два отличия. Необходимо получить изображение **хранилище/microsoft/mssql-server-linux:\<имя тега\>**  магазине Docker. При этом необходимо указать производственного выпуска с **MSSQL_PID** переменной среды. Приведенный ниже показано, как выполнять последний образ контейнера 2017 г. SQL Server Enterprise Edition:



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-encrypting-connections-to-sql-server-on-linuxsql-server-linux-encrypted-connectionsmd"></a>5. &nbsp;[Зашифрованных подключениях к SQL Server в Linux](sql-server-linux-encrypted-connections.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_4) | [Далее](#TitleNum_6))

<!-- Source markdown line 45.  ms.author= meetb;rickbyh.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7e3187866df060903e30000d60d673edad46d210 bcb1f2771e6c29b535a30b9f23ac296954509187  (PR=4150  ,  Filename=sql-server-linux-encrypted-connections.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



        sudo chown mssql:mssql mssql.pem mssql.key
        sudo chmod 600 mssql.pem mssql.key
        sudo mv mssql.pem /etc/ssl/certs/
        sudo mv mssql.key /etc/ssl/private/

- **Настройка SQL Server**

        systemctl stop mssql-server
        cat /var/opt/mssql/mssql.conf
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0

- **Регистрация сертификата на клиентском компьютере (Windows, Linux или macOS)**

    -   При использовании сертификата, подписанного ЦС, вам необходимо скопировать сертификат центра сертификации (ЦС) вместо сертификата пользователя на клиентском компьютере.
    -   Если используется самозаверяющий сертификат, просто скопируйте PEM-файл следующие папки, соответствующей для распространения и выполнять команды для их включения

        - **Windows**: Импорт PEM-файл в качестве сертификата в папке current user "->" Доверенные корневые центры сертификации -> сертификаты
        - **macOS**:

-   **Примеры строк подключения**

    - **..! ДОБАВИТЬ NotShown--ssmanstudiofull md--... /includes/ssManStudioFull-MD.MD)]** ! [ Среда SSMS подключения dialog--media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png» SSMS диалоговое окно соединения»)



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-create-and-run-sql-server-agent-jobs-on-linuxsql-server-linux-run-sql-server-agent-jobmd"></a>6. &nbsp;[Создания и выполнения заданий агента SQL Server в Linux](sql-server-linux-run-sql-server-agent-job.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_5) | [Далее](#TitleNum_7))

<!-- Source markdown line 35.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1598129bb5f98434435d8ad02336a9adf76c7870 6fe3fe7df3a60dbac31f1df59aac9860d293421a  (PR=4150  ,  Filename=sql-server-linux-run-sql-server-agent-job.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



С этим учебником требуются следующие необходимые компоненты:

* Компьютер Linux со следующими компонентами:
  * SQL Server 2017 г. ([RHEL--quickstart-install-connect-red-hat.md), [SLES — краткое руководство install подключения suse.md), или [Ubuntu — краткое руководство install подключения ubuntu.md)) с помощью средства командной строки.

Следующие компоненты являются необязательными.

* Компьютер Windows с помощью SSMS:
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) для дополнительных шагов SSMS.

**Установка агента SQL Server**


Чтобы использовать агент SQL Server в Linux, необходимо сначала установить **mssql-server-agent** пакета на компьютере, на котором уже установлен 2017 г. SQL Server.

1. Установка **mssql-server-agent** с команду, соответствующую операционной системе Linux.

   | Платформа | Выполнение команд установки |
   |-----|-----|
   | RHEL | `sudo yum install mssql-server-agent` |
   | SLES | `sudo zypper refresh`<br/>`sudo zypper update mssql-server-agent` |
   | Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server-agent` |

1. Перезапустите SQL Server с помощью следующей команды:

```
   sudo systemctl restart mssql-server
```

**Создание образца базы данных**


Выполните следующие действия для создания образца базы данных с именем **SampleDB**. Эта база данных используется для ежедневного задания резервного копирования.

1. На компьютере Linux откройте сеанс терминала bash.



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-installation-guidance-for-sql-server-on-linuxsql-server-linux-setupmd"></a>7. &nbsp;[Руководство по установке для SQL Server в Linux](sql-server-linux-setup.md)

*Обновлено: 2017 г-12-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_6) | [Далее](#TitleNum_8))

<!-- Source markdown line 125.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8ba2bf6f9cf4b5f54a6ee0f4d16d4437d5724880 eedddcfb64c6432215f56b74dc91700d9804fce8  (PR=4160  ,  Filename=sql-server-linux-setup.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=085dd05d56afecbb454206ed8402cfbaa597cfbe) -->



**<a id="repositories"></a>Настройка исходных репозиториев**


При установке или обновлении SQL Server, можно получить последнюю версию SQL Server из репозитория настроенных Microsoft.

**Параметры хранилища**


Существует два основных типа хранилища для каждого распределения.

- **Накопительный пакет обновления (CU)**: репозиторий накопительное обновление (CU) содержит пакеты для базовой версии SQL Server и исправления или улучшения версии. Накопительные пакеты обновления относятся только к версии, например 2017 г. SQL Server. Их появления в обычных ритме.

- **GDR**: GDR репозитория пакетов для базовой версии SQL Server и только важные исправления и обновления для системы безопасности содержит версии. Эти обновления также добавляются в следующий выпуск CU.

Каждое CU и GDR содержит полный пакет SQL Server и все последующие обновления для этого репозитория. Обновление с версии GDR на текущую версию поддерживается изменение настроенного хранилища SQL Server. Вы также можете [понизить--#rollback) для любого из выпусков в ваш основной номер версии (например: 2017 г.). Обновление с накопительным пакетом обновления версии GDR не поддерживается.

**Проверьте настроенные репозиторий**


Если вы хотите проверить настроен репозиторий, используйте следующие методики зависят от платформы.

| Платформа | Процедура |
|-----|-----|
| RHEL | 1. Просматривать файлы в **/etc/yum.repos.d** каталога:`sudo ls /etc/yum.repos.d`<br/>2. Найдите файл, который настраивает каталог SQL Server, такие как **mssql server.repo**.<br/>3. Распечатать содержимое файла:`sudo cat /etc/yum.repos.d/mssql-server.repo`<br/>4. **Имя** свойство является настроенного репозитория.|
| SLES | 1. Выполните следующую команду:`sudo zypper info mssql-server`<br/>2. **Репозитория** свойство является настроенного репозитория. |
| Ubuntu | 1. Выполните следующую команду:`sudo cat /etc/apt/sources.list`<br/>2. Проверьте URL-адреса для сервера mssql пакета. |



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-configure-failover-cluster-instance---sql-server-on-linux-rhelsql-server-linux-shared-disk-cluster-configuremd"></a>8. &nbsp;[Настроить отказоустойчивый кластер — SQL Server для Linux (RHEL)](sql-server-linux-shared-disk-cluster-configure.md)

*Обновлено: 2017 г-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([предыдущих](#TitleNum_7) | [Далее](#TitleNum_9))

<!-- Source markdown line 25.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 308fa1809c80a009f7f15b5ca6917f6b76588c3e 71f18baa320041ff10c94e8c7668e40dff45cac3  (PR=4150  ,  Filename=sql-server-linux-shared-disk-cluster-configure.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



> [!div class="checklist"]
> * Установка и настройка Linux
> * Установка и настройка SQL Server
> * Настройка файла hosts
> * Настройка общего хранилища и перемещение файлов базы данных
> * Установка и настройка Pacemaker на каждом узле кластера
> * Настройка экземпляра отказоустойчивого кластера

В этой статье описывается создание экземпляра отказоустойчивого кластера общего диска с двумя узлами (FCI) для SQL Server. В статье содержатся инструкции и примеры сценариев для Red Hat Enterprise Linux (RHEL). Ubuntu распределения похожи на RHEL, поэтому обычно будут примеры сценариев работы с Ubuntu.

Основные сведения см. в разделе [SQL Server экземпляр (Отказоустойчивого кластера) на Linux--sql-server-linux-shared-disk-cluster-concepts.md).

**Предварительные требования**


Для выполнения сценария конца в конец ниже требуется две машины для развертывания двух узлов кластера и другой сервер для хранения. Шаги, описанные ниже описываются настройки этих серверов.

**Установка и настройка Linux**


Первым шагом является настройка операционной системы на узлах кластера. На каждом узле в кластере настройте ОС Linux. Используйте те же распространения и версии на обоих узлах. Используйте одно из них, распределений следующие:

* RHEL с действительной подпиской для надстройки высокого уровня ДОСТУПНОСТИ

**Установка и настройка SQL Server**


1. Установка и настройка SQL Server на обоих узлах.  Подробные инструкции см. [установка SQL Server в Linux--sql server-linux setup.md).
1. Назначить один узел в качестве основной, а другой — как получателя для целей конфигурации. Использовать эти термины для следующих в этом руководстве.
1. На вторичном узле остановите и отключите SQL Server.
    В следующем примере останавливается и отключает SQL Server:
```
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
```

    > [!NOTE]
    > At set up time, a Server Master Key is generated for the SQL Server instance and placed at `var/opt/mssql/secrets/machine-key`. On Linux, SQL Server always runs as a local account called mssql. Because it's a local account, its identity isn't shared across nodes. Therefore, you need to copy the encryption key from primary node to each secondary node so each local mssql account can access it to decrypt the Server Master Key.



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-troubleshoot-sql-server-on-linuxsql-server-linux-troubleshooting-guidemd"></a>9. &nbsp;[Устранения неполадок SQL Server в Linux](sql-server-linux-troubleshooting-guide.md)

*Обновлено: 30.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_8))

<!-- Source markdown line 125.  ms.author= anshrest.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5f8557a34b38e028ff6e5ac370b6d2d6bf315091 196e56187b57bdd79cc5cdc5e6fce3d41e82af0c  (PR=4150  ,  Filename=sql-server-linux-troubleshooting-guide.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



**Запуск SQL Server в минимальной конфигурации или в однопользовательском режиме**


**Запуск SQL Server в режиме минимальной конфигурации**

Эта функция полезна в случае, если установленные значения конфигурации (например, слишком большой объем выделяемой памяти) не позволяют выполнить запуск сервера.

```
   sudo -u mssql /opt/mssql/bin/sqlservr -f
```

**Запуск SQL Server в однопользовательском режиме**

В некоторых случаях может потребоваться запустить экземпляр SQL Server в однопользовательском режиме, используя параметр запуска -m. Например, может понадобиться изменить параметры конфигурации сервера, восстановить поврежденную базу данных master или другую системную базу данных. Например может потребоваться изменить параметры конфигурации сервера или восстановить поврежденную базу данных master или другую системную базу данных

Запуск SQL Server в однопользовательском режиме
```
   sudo -u mssql /opt/mssql/bin/sqlservr -m
```

Запуск SQL Server в однопользовательском режиме с помощью SQLCMD
```
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
```

> [!WARNING]
>  Чтобы избежать проблем с запуском в дальнейшем, SQL Server в Linux следует запускать с указанием пользователя "mssql". Пример: "sudo -u mssql /opt/mssql/bin/sqlservr [параметры запуска]"

Если вы случайно начали SQL Server с другим пользователем, необходимо будет изменить владельца файлов базы данных SQL Server для пользователя «mssql» перед запуском SQL Server с systemd. Например для изменения владельца всех файлов базы данных в группе /var/opt/mssql для пользователя «mssql», выполните следующую команду

```
   chown -R mssql:mssql /var/opt/mssql/
```







## <a name="similar-articles"></a>Аналогичные статей

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметных областей, которые имеют новые или недавно обновленные статьи

- [Новые + обновленные (3+14): **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (1 + 0): **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (87+0): **Analytics Platform System для SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (5+4): **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+1): **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (2+2): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (10+9): **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (2+4): **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (4+2): **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (0+1): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (21+0): **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(5+1): **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (0 + 1): **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (1+0): **Помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новый + обновленные (0 + 1): **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2): **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметных областей, в которых нет новых или недавно обновленных статей

- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новый + обновленные (0 + 0): **объектов данных ActiveX (ADO) для SQL** документы](../ado/new-updated-ado.md)
- [Новый + обновленные (0 + 0): **Data Quality Services для SQL** документы](../data-quality-services/new-updated-data-quality-services.md)
- [Новый + обновленные (0 + 0): **расширений интеллектуального анализа (DMX) для SQL** документы](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новый + обновленные (0 + 0): **многомерных выражений (MDX) для SQL** документы](../mdx/new-updated-mdx.md)
- [Новый + обновленные (0 + 0): **ODBC (Open Database Connectivity) для SQL** документы](../odbc/new-updated-odbc.md)
- [Новый + обновленные (0 + 0): **PowerShell для SQL** документы](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новый + обновленные (0 + 0): **XQuery для SQL** документы](../xquery/new-updated-xquery.md)


