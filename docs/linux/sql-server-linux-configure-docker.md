---
title: Параметры конфигурации для 2017 г. SQL Server на Docker | Документы Microsoft
description: Возможность использования различных способов использования и взаимодействия с образами контейнеров 2017 г. SQL Server в Docker. Это включает сохранение, копирование файлов и устранения неполадок.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/26/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.custom: sql-linux
ms.openlocfilehash: 57c3ed3a87f11d0079a18b9906459117cf67c8b9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="configure-sql-server-2017-container-images-on-docker"></a>Настройка образов контейнеров 2017 г. SQL Server на Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье объясняется, как настроить и использовать [образ контейнера mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) с помощью Docker. Этот образ содержит SQL Server, работающий в системе Linux, основанной на Ubuntu 16.04. Он может использоваться с Dосker Engine 1.8+ на Linux или Docker для Mac или Windows.

> [!NOTE]
> В этой статье особое внимание уделяется с помощью образа mssql-server-linux. Непокрытые образа Windows, но Дополнительные сведения о нем на [Docker Hub страница windows для сервера mssql](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a name="pull-and-run-the-container-image"></a>Извлечение и запуск образа контейнера

Для извлечения и запустить образ контейнера Docker для 2017 г. SQL Server, выполните необходимые условия и действия, описанные в следующем кратком руководстве.

- [Запускать образ контейнера 2017 г. SQL Server с помощью Docker](quickstart-install-connect-docker.md)

Конфигурации также приводятся сценарии использования дополнительных в следующих разделах.

## <a id="production"></a> Запустите производственного образы контейнеров

Краткое руководство, в предыдущем разделе выполняется бесплатный выпуск SQL Server Developer из Docker Hub. Большая часть информации по-прежнему применяется в том случае, если вы хотите запустить производства образы контейнеров, таких как выпуски Enterprise, Standard или Web. Однако существуют некоторые различия, которые здесь описаны.

- SQL Server можно использовать в производственной среде, только если у вас есть действительная лицензия. Можно получить бесплатную лицензию SQL Server Express рабочей [здесь](https://go.microsoft.com/fwlink/?linkid=857693). Лицензии SQL Server Standard и Enterprise Edition доступны через [корпоративного лицензирования Майкрософт](https://www.microsoft.com/Licensing/licensing-programs/licensing-programs.aspx).

- Образы контейнеров рабочей среде SQL Server должны извлекаться с [Docker хранилище](https://store.docker.com). Если вы уже нет, создайте учетную запись в хранилище Docker.

- Образ контейнера разработчика в магазине Docker можно настроить для запуска в выпусках производства. Для запуска рабочей версии, выполните следующие действия:

   1. Во-первых Войдите на свой идентификатор docker из командной строки.

      ```bash
      docker login
      ```

   1. Далее необходимо для получения бесплатной разработчик образ контейнера в хранилище Docker. Последовательно выберите пункты [ https://store.docker.com/images/mssql-server-linux ](https://store.docker.com/images/mssql-server-linux), нажмите кнопку **продолжить извлечение**и следуйте инструкциям.

   1. Просмотрите требования и процедуры [краткое руководство](quickstart-install-connect-docker.md). Однако имеются два отличия. Необходимо получить изображение **хранилище/microsoft/mssql-server-linux:\<имя тега\>**  магазине Docker. При этом необходимо указать производственного выпуска с **MSSQL_PID** переменной среды. Приведенный ниже показано, как выполнять последний образ контейнера 2017 г. SQL Server Enterprise Edition:

      ```bash
      docker run --name sqlenterprise \
         -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
         -e 'MSSQL_PID=Enterprise' -p 1433:1433 \
         -d store/microsoft/mssql-server-linux:2017-latest
      ```

      ```PowerShell
      docker run --name sqlenterprise `
         -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
         -e "MSSQL_PID=Enterprise" -p 1433:1433 `
         -d "store/microsoft/mssql-server-linux:2017-latest"
      ```

      > [!IMPORTANT]
      > Путем передачи значения **Y** для переменной среды **ACCEPT_EULA** и значение edition **MSSQL_PID**, вы выражаете наличие допустимым и существующих лицензию выпуск и версия SQL Server, которую планируется использовать. Вы также соглашаетесь с тем, что использование программного обеспечения SQL Server, работающих в образ контейнера Docker, подпадают под условия лицензии SQL Server.

      > [!NOTE]
      > Полный список возможных значений для **MSSQL_PID**, в разделе [SQL Server можно настроить параметры с переменными среды на Linux](sql-server-linux-configure-environment-variables.md).

## <a name="connect-and-query"></a>Подключения и запроса

Можно подключиться и запросов SQL Server в контейнере с либо вне контейнера или в контейнере. В следующих разделах объясняется оба сценария. 

### <a name="tools-outside-the-container"></a>Средства вне контейнера

Можно соединиться с экземпляром SQL Server на компьютере Docker с помощью любого внешнего средства macOS, Windows или Linux, поддерживающее подключения SQL. Некоторые общие средства включают:

- [программа sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md);
- [SQL Server Management Studio (SSMS) в Windows](sql-server-linux-develop-use-ssms.md);

В следующем примере используется **sqlcmd** для подключения к SQL Server, запущенный в контейнер Docker. IP-адреса в строке подключения является IP-адрес компьютера, на котором выполняется контейнера.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Порт узла, который не был по умолчанию был сопоставлен **1433**, добавьте этот порт в строке подключения. Например, если вы указали `-p 1400:1433` в вашей `docker run` команды, а затем соедините с явным образом указать порт 1400.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Средства внутри контейнера

Начиная с SQL Server 2017 г CTP 2.0 [средства командной строки SQL Server](sql-server-linux-setup-tools.md) включаются в образе контейнера. При присоединении к образу с интерактивной командной строки средства можно выполнять локально.

1. Выполните команду `docker exec -it`, чтобы запустить интерактивную оболочку bash внутри запущенного контейнера. В следующем примере `e69e056c702d` — это идентификатор контейнера.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Не всегда необходимо указывать идентификатор весь контейнер. Необходимо указать достаточно символов, для его однозначной идентификации. Поэтому в этом примере может быть достаточно, чтобы использовать `e6` или `e69` вместо полного идентификатора.

2. После входа в контейнер подключитесь локально с помощью sqlcmd. Обратите внимание, что sqlcmd не в пути по умолчанию, поэтому необходимо указать полный путь.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. После завершения работы с sqlcmd, введите `exit`.

4. После завершения работы с интерактивной командной строки, введите `exit`. Контейнер продолжит работать после выхода из интерактивной оболочки bash.

## <a name="run-multiple-sql-server-containers"></a>Запустите несколько контейнеров SQL Server

Docker обеспечивает возможность запуска несколько контейнеров SQL Server на том же компьютере узла. Этот подход для сценариев, требующих несколько экземпляров SQL Server на том же узле. Каждый контейнер должен предоставлять сам на другой порт.

В следующем примере создаются два контейнера SQL Server и сопоставляет их с порты **1401** и **1402** на хост-компьютере.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d microsoft/mssql-server-linux:2017-latest
```

Теперь имеются два экземпляра SQL Server, запущенный в отдельные контейнеры. Клиенты могут подключаться к каждому экземпляру SQL Server с помощью IP-адрес узла Docker и номер порта для контейнера.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="persist"></a> Сохранить данные

Изменения конфигурации SQL Server и файлы базы данных сохраняются в контейнере даже при перезагрузке контейнер с `docker stop` и `docker start`. Однако если удалить контейнер с `docker rm`, все данные в контейнере удаляются, включая SQL Server и баз данных. Следующий раздел объясняет, как использовать **тома данных** для сохранения файла базы данных, даже если удалены связанные контейнеры.

> [!IMPORTANT]
> Для SQL Server очень важно понимать сохранение данных в Docker. Помимо обсуждения в этом разделе, в документации Docker на [управление данными в контейнерах Docker](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Подключить узел каталога в качестве тома данных

Первый параметр — подключение к каталогу на узле в качестве тома данных в контейнере. Чтобы сделать это, используйте `docker run` с `-v <host directory>:/var/opt/mssql` флаг. Это позволяет данные для восстановления между выполнениями контейнера.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

Этот метод дает возможность совместного использования и просматривать файлы на узле за пределами Docker.

> [!IMPORTANT]
> Сопоставление тома узла для Docker на Mac с SQL Server на образе Linux в настоящее время не поддерживается. Вместо этого используйте контейнеры томов данных. Это ограничение относится только к `/var/opt/mssql` каталога. Чтение из подключенного каталога работает нормально. Например можно подключить узла каталога, с ключом-v на Mac и восстановление резервной копии из BAK-файл, который находится на узле.

### <a name="use-data-volume-containers"></a>Используйте контейнеры томов данных

Второй вариант — использовать контейнер томов данных. Можно создать контейнер томов данных, указав имя тома вместо каталог узла с `-v` параметра. В следующем примере создается общего тома данных с именем **sqlvolume**.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

> [!NOTE]
> Этот метод для выполнения команды неявно создания тома данных не работает с более ранними версиями Docker. В этом случае использовать явную шаги, описанные в документации Docker [Создание и подключение контейнера томов данных](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Даже в том случае, если остановить и удалить этот контейнер, тома данных не будет устранена. Вы можете просмотреть ее с `docker volume ls` команды.

```bash
docker volume ls
```

При создании другой контейнер с тем же именем тома новый контейнер использует те же данные SQL Server, находящиеся на томе.

Чтобы удалить контейнер томов данных, используйте `docker volume rm` команды.

> [!WARNING]
> При удалении контейнера томов данных, все данные SQL Server, в контейнере, *окончательно* удалены.

### <a name="backup-and-restore"></a>Резервное копирование и восстановление

Помимо этих методов контейнера можно также использовать стандартные резервного копирования SQL Server и восстановить методы. Файлы резервных копий можно использовать для защиты данных или перемещения данных на другой экземпляр SQL Server. Дополнительные сведения см. в разделе [резервное копирование и восстановление баз данных SQL Server в Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> При создании резервных копий, убедитесь, что для создания или копирования файлов резервной копии вне контейнера. В противном случае при удалении контейнера также удаляются файлы резервной копии.

## <a name="execute-commands-in-a-container"></a>Выполнение команд в контейнер

При наличии запущенного контейнера из узла терминалов позволяет выполнять команды в контейнере.

Чтобы получить идентификатор контейнера запуска:

```bash
docker ps
```

Чтобы запустить bash, терминалов в контейнере запуска:

```bash
docker exec -ti <Container ID> /bin/bash
```

Теперь можно выполнить команды, как если бы, если вы используете их терминалов внутри контейнера. По завершении введите `exit`. Это завершает работу во время сеанса интерактивной командой, но продолжает выполняться контейнера.

## <a name="copy-files-from-a-container"></a>Скопируйте файлы из контейнера

Чтобы скопировать файл из контейнера, используйте следующую команду:

```bash
docker cp <Container ID>:<Container path> <host path>
```

**Пример:**

```bash
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog /tmp/errorlog
```

```PowerShell
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog C:\Temp\errorlog
```

## <a name="copy-files-into-a-container"></a>Скопируйте файлы в контейнер

Чтобы скопировать файл в контейнер, используйте следующую команду:

```bash
docker cp <Host path> <Container ID>:<Container path>
```

**Пример:**

```bash
docker cp /tmp/mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

```PowerShell
docker cp C:\Temp\mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

## <a name="run-a-specific-sql-server-container-image"></a>Запустите конкретных образа контейнера SQL Server

Существуют сценарии, где вы не можете использовать последний образ контейнера SQL Server. Для выполнения конкретных образа контейнера SQL Server, выполните следующие действия:

1. Определить Docker **тега** для выпуска, который вы хотите использовать. Просмотреть доступные теги [страница концентратора Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. По запросу образ контейнера SQL Server с тегом. Например, для извлечения изображения RC1, замените `<image_tag>` в следующую команду с `rc1`.

   ```bash
   docker pull microsoft/mssql-server-linux:<image_tag>
   ```

1. Чтобы запустить новый контейнер с изображением, укажите имя тега в `docker run` команды. В следующей команде замените `<image_tag>` с версией, требуется запустить.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
   ```

Эти действия также можно понизить существующий контейнер. Например вы хотите выполнить откат или понизить запущенного контейнера для устранения неполадок или тестирование. Чтобы понизить запущенного контейнера, необходимо использовать метод сохраняемости на папку данных. Выполните те же действия, описанные в [обновите раздел](#upgrade), но указать имя тега для более ранней версии, при запуске нового контейнера.

> [!IMPORTANT]
> Обновление и переход к более раннему поддерживаются только между RC1 и RC2 в данный момент.

## <a id="upgrade"></a> Обновление SQL Server в контейнерах

Чтобы обновить образ контейнера с помощью Docker, сначала найдите тег для выпуска для обновления. Эта версия по запросу из реестра с `docker pull` команды:

```bash
docker pull microsoft/mssql-server-linux:<image_tag>
```

Это обновляет образ SQL Server для любой новые контейнеры, создаваемые вами, но не обновляет SQL Server в все запущенные контейнеры. Для этого необходимо создать новый контейнер в образе контейнера последнюю SQL Server и перенести данные в этот новый контейнер.

1. Убедитесь, что вы используете один из [методы сохраняемости данных](#persist) для существующего контейнера SQL Server. Это позволяет запустить новый контейнер с теми же данными.

1. Остановка SQL Server контейнер с `docker stop` команды.

1. Создать новый контейнер SQL Server с `docker run` и указать каталог сопоставленных узла или контейнер томов данных. Убедитесь в том использовать специальный тег для обновления SQL Server. Новый контейнер теперь использует новую версию SQL Server с помощью существующих данных SQL Server.

   > [!IMPORTANT]
   > Обновление поддерживается только между RC1, RC2 и общедоступной версии в настоящее время.

1. Проверка баз данных и данных в новый контейнер.

1. При необходимости удалите старый контейнер с `docker rm`.

## <a id="troubleshooting"></a> Устранение неполадок

В следующих разделах содержатся сведения об устранении неполадок для запуска SQL Server в контейнерах.

### <a name="docker-command-errors"></a>Ошибки команды docker

Если возникли ошибки для любой `docker` команды, убедитесь, что запущена служба docker и попробуйте выполнить с повышенными разрешениями.

Например, в Linux, может появиться следующая ошибка при выполнении `docker` команды:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Если эта ошибка появляется в Linux, попытайтесь выполнить те же команды, предваряемые фразой `sudo`. В случае неудачи, проверьте, запущена служба docker и запустить его при необходимости.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

В Windows убедитесь, что вы выполняете запуск PowerShell или в командной строке с правами администратора.

### <a name="sql-server-container-startup-errors"></a>Ошибки при запуске контейнера SQL Server

Если контейнер SQL Server не запускается, выполните следующие проверки.

- Если появляется сообщение об ошибке, таких как **"не удалось создать конечную точку CONTAINER_NAME сетевой мост. Ошибка при запуске прокси-сервера: привязка 0.0.0.0:1433 прослушивания tcp: адрес уже используется. "** , а затем пытаетесь сопоставление контейнера порта 1433 порт, который уже используется. Это может произойти, если вы используете SQL Server локально на хост-компьютере. Он также может произойти, если запустить два контейнера SQL Server и сопоставьте их оба на один и тот же порт узла. В этом случае используйте `-p` параметр для сопоставления портов другой узел контейнера порт 1433. Например: 

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d microsoft/mssql-server-linux:2017-latest`.
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d microsoft/mssql-server-linux:2017-latest`.
    ```

- Проверьте, есть ли сообщения об ошибках из контейнера.

    ```bash
    docker logs e69e056c702d
    ```

- Убедитесь, что выполняются минимальные требования памяти и диска, указанное в [требования](#requirements) этого раздела.

- Если вы используете программное обеспечение управления контейнера, убедитесь, что он поддерживает контейнера процессы, выполняющиеся как корневой. Процесс sqlservr в контейнере работает как корень.

- Просмотрите [SQL Server программа установки и журналы ошибок](#errorlogs).

### <a name="enable-dump-captures"></a>Включить снимки дампа

Если произошел сбой процесса SQL Server внутри контейнера, необходимо создать новый контейнер с **SYS_PTRACE** включена. Это добавляет Linux возможность трассировки процесса, который необходим для создания файла дампа при возникновении исключения. Файл дампа может использоваться службой поддержки для помощи в устранении проблемы. Следующей командой docker run включающий эту возможность.

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
```

### <a name="sql-server-connection-failures"></a>Сбоев соединений SQL Server

Если не удается подключиться к экземпляру SQL Server, запускается в контейнере, выполните следующие проверки.

- Убедитесь, что контейнер SQL Server запущена, просмотрев **состояние** столбец `docker ps -a` выходных данных. В противном случае используйте `docker start <Container ID>` для его запуска.

- При сопоставлении узла нестандартный порт (не 1433), убедитесь, что порт указываются в строке подключения. Вы увидите сопоставление порта на **ПОРТЫ** столбец `docker ps -a` выходных данных. Например следующая команда выполняет подключение sqlcmd в контейнер, который прослушивает порт 1401:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Если вы использовали `docker run` с существующие тома сопоставленных данных или контейнер томов данных, SQL Server игнорирует значение `MSSQL_SA_PASSWORD`. Вместо этого используется предварительно настроенный пароль пользователя SA, из данных SQL Server в том или данных контейнера томов данных. Убедитесь, что вы используете пароль SA, связанные с данными, которые вы присоединения.

- Просмотрите [SQL Server программа установки и журналы ошибок](#errorlogs).

### <a name="sql-server-availability-groups"></a>Группы доступности SQL Server

При использовании Docker с группами доступности SQL Server существует два дополнительных требований.

- Сопоставление порта, который используется для связи реплика (по умолчанию 5022). Например, указать `-p 5022:5022` как часть вашего `docker run` команды.

- Явно задать имя узла контейнера с `-h YOURHOSTNAME` параметр `docker run` команды. Это имя узла используется при настройке группы доступности. Если не указать его с `-h`, по умолчанию используется идентификатор контейнера.

### <a id="errorlogs"></a> SQL Server программа установки и журналы ошибок

Вы можете просмотреть программы установки SQL Server и журналы ошибок **/var/opt/mssql/log**. Если контейнер не запущена, сначала запустите контейнер. Затем используйте интерактивной командной строки, чтобы просмотреть журналы.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

Из сеанса bash внутри контейнера выполните следующие команды:

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Если подключить каталога сервера **/var/opt/mssql** при создании контейнера, вместо этого можно осуществлять **журнала** подкаталог на сопоставленном путь на узле.

## <a name="next-steps"></a>Следующие шаги

Начало работы с образами контейнеров 2017 г. SQL Server на Docker через [краткое руководство](quickstart-install-connect-docker.md).

См. также, [mssql docker репозитории GitHub](https://github.com/Microsoft/mssql-docker) ресурсы, отзывы и известные проблемы.
