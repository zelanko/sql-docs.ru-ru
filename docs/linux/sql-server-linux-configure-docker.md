---
title: Параметры конфигурации для SQL Server в DOCKER
description: Изучите различные способы использования и взаимодействия с изображениями контейнеров SQL Server 2017 и 2019 Preview в DOCKER. Сюда входят сохранение данных, копирование файлов и устранение неполадок.
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: d24bb3566195c71a3b62d16fab867ab5085404b7
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388379"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Настройка образов контейнеров SQL Server в DOCKER

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье объясняется, как настроить и использовать [образ контейнера MSSQL-Server-Linux](https://hub.docker.com/_/microsoft-mssql-server) с DOCKER. Этот образ содержит SQL Server, работающий в системе Linux, основанной на Ubuntu 16.04. Он может использоваться с Dосker Engine 1.8+ на Linux или Docker для Mac или Windows.

> [!NOTE]
> В этой статье особое внимание уделяется использованию образа MSSQL-Server-Linux. Образ Windows не охватывается, но вы можете получить дополнительные сведения о нем на [странице центра MSSQL-Server-Windows DOCKER](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a name="pull-and-run-the-container-image"></a>Извлечение и запуск образа контейнера

Чтобы извлечь и запустить образы контейнеров DOCKER для SQL Server 2017 и SQL Server 2019 (Предварительная версия), выполните предварительные требования и действия, описанные в следующем кратком руководстве.

- [Запуск образа контейнера SQL Server 2017 с помощью DOCKER](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Запуск образа контейнера предварительной версии SQL Server 2019 с помощью DOCKER](quickstart-install-connect-docker.md?view=sql-server-ver15)

Эта статья о конфигурации содержит дополнительные сценарии использования в следующих разделах.

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a>Запуск образов контейнеров на основе RHEL

Вся документация по SQL Server образов контейнеров Linux указывает на контейнеры на основе Ubuntu. Начиная с предварительной версии SQL Server 2019 можно использовать контейнеры на основе Red Hat Enterprise Linux (RHEL). Измените репозиторий контейнеров с **MCR.Microsoft.com/MSSQL/Server:2019-CTP3.1-Ubuntu** на **MCR.Microsoft.com/MSSQL/RHEL/Server:2019-CTP3.1** во всех командах DOCKER.

Например, следующая команда извлекает последний контейнер предварительной версии SQL Server 2019, использующий RHEL:

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a>Запуск образов рабочих контейнеров

В кратком руководстве в предыдущем разделе выполняется бесплатный выпуск Developer SQL Server из DOCKER Hub. Большая часть информации по-прежнему применима, если вы хотите запускать рабочие образы контейнеров, такие как выпуски Enterprise, Standard или Web. Однако существует несколько отличий, описанных здесь.

- Вы можете использовать только SQL Server в рабочей среде, если у вас есть действительная лицензия. Бесплатную SQL Server Express производственной лицензии можно получить [здесь](https://go.microsoft.com/fwlink/?linkid=857693). Лицензии SQL Server Standard и Enterprise Edition доступны по [программе корпоративного лицензирования Майкрософт](https://www.microsoft.com/licensing/default.aspx).


- Образ контейнера разработчика можно настроить так, чтобы он также выполнял рабочие выпуски. Для запуска рабочих выпусков выполните следующие действия.

Ознакомьтесь с требованиями и выполните процедуры в [кратком руководстве](quickstart-install-connect-docker.md). Необходимо указать рабочую версию с переменной среды **MSSQL_PID** . В следующем примере показано, как запустить последнюю версию образа контейнера SQL Server 2017 для выпуска Enterprise:

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
> Передав значение **Y** переменной среды **ACCEPT_EULA** и значению выпуска **MSSQL_PID**, вы выражаете, что у вас есть действительная и существующая лицензия для выпуска и версии SQL Server, которую предполагается использовать. Вы также соглашаетесь с тем, что использование программного обеспечения SQL Server, работающего в образе контейнера DOCKER, регулируется условиями лицензии на SQL Server.

> [!NOTE]
> Полный список возможных значений для **MSSQL_PID**см. в статье [Настройка параметров SQL Server с помощью переменных среды в Linux](sql-server-linux-configure-environment-variables.md).

::: moniker-end

## <a name="connect-and-query"></a>Подключение и запрос

Можно подключаться и запрашивать SQL Server в контейнере вне контейнера или в контейнере. В следующих разделах описываются оба сценария. 

### <a name="tools-outside-the-container"></a>Средства вне контейнера

Вы можете подключиться к экземпляру SQL Server на компьютере DOCKER из любого внешнего средства Linux, Windows или macOS, поддерживающего подключения SQL. Ниже перечислены некоторые распространенные средства.

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md);
- [SQL Server Management Studio (SSMS) в Windows](sql-server-linux-manage-ssms.md);

В следующем примере программа **sqlcmd** используется для подключения к SQL Server, работающей в контейнере DOCKER. IP-адрес в строке подключения — это IP-адрес главного компьютера, на котором выполняется контейнер.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Если вы сопоставили порт узла, который не является значением по умолчанию **1433**, добавьте этот порт в строку подключения. Например, если вы указали `-p 1400:1433` `docker run` в команде, подключитесь, явно указав порт 1400.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Средства внутри контейнера

Начиная с предварительной версии SQL Server 2017, [средства командной строки SQL Server](sql-server-linux-setup-tools.md) включены в образ контейнера. Если вы подключаетесь к образу с помощью интерактивной командной строки, вы можете запускать средства локально.

1. Выполните команду `docker exec -it`, чтобы запустить интерактивную оболочку bash внутри запущенного контейнера. В следующем примере `e69e056c702d` показан идентификатор контейнера.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Не всегда нужно указывать весь идентификатор контейнера. Необходимо указать достаточное количество символов для уникальной идентификации. Поэтому в этом примере может быть достаточно, чтобы использовать `e6` или `e69` , а не полный идентификатор.

2. После входа в контейнер подключитесь локально с помощью sqlcmd. Обратите внимание, что программа sqlcmd не находится в пути по умолчанию, поэтому необходимо указать полный путь.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. По завершении работы с sqlcmd `exit`введите.

4. После завершения работы с интерактивной командной строкой введите `exit`. Контейнер продолжит работать после выхода из интерактивной оболочки bash.

## <a name="run-multiple-sql-server-containers"></a>Запуск нескольких контейнеров SQL Server

DOCKER предоставляет способ запуска нескольких контейнеров SQL Server на одном хост-компьютере. Это подход для сценариев, требующих наличия нескольких экземпляров SQL Server на одном узле. Каждый контейнер должен предоставлять себя на другом порте.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В следующем примере создаются два контейнера SQL Server 2017 и сопоставляются порты **1401** и **1402** на размещающем компьютере.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

В следующем примере создаются два контейнера предварительной версии SQL Server 2019 и сопоставляются порты **1401** и **1402** на размещающем компьютере.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

Теперь существует два экземпляра SQL Server, работающих в отдельных контейнерах. Клиенты могут подключаться к каждому экземпляру SQL Server с помощью IP-адреса узла DOCKER и номера порта для контейнера.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a>Создание настраиваемого контейнера

Можно создать собственный [Dockerfile](https://docs.docker.com/engine/reference/builder/#usage) , чтобы создать настраиваемый контейнер SQL Server. Дополнительные сведения см. [в демонстрационной версии, объединяющей SQL Server и приложение Node](https://github.com/twright-msft/mssql-node-docker-demo-app). Если вы создаете собственный Dockerfile, учитывайте процесс переднего плана, так как этот процесс управляет жизненным циклом контейнера. Если он завершает работу, контейнер завершает работу. Например, если вы хотите запустить сценарий и запустить SQL Server, убедитесь, что SQL Server процесс является самой правой командой. Все остальные команды выполняются в фоновом режиме. Это показано в следующей команде в Dockerfile:

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

Если вы отменяете команды в предыдущем примере, контейнер завершит работу после завершения сценария do-my-sql-commands.sh.

## <a id="persist"></a>Сохранение данных

Изменения конфигурации SQL Server и файлы базы данных сохраняются в контейнере даже при перезапуске контейнера с помощью `docker stop` и. `docker start` Однако если удалить контейнер с помощью `docker rm`, все контейнеры удаляются, включая SQL Server и базы данных. В следующем разделе объясняется, как использовать **тома данных** для сохранения файлов базы данных, даже если связанные контейнеры удалены.

> [!IMPORTANT]
> Для SQL Server важно понимать сохранность данных в DOCKER. В дополнение к обсуждению в этом разделе см. документацию по DOCKER о [том, как управлять данными в контейнерах DOCKER](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Подключение каталога узлов в качестве тома данных

Первый вариант — подключить каталог на узле в качестве тома данных в контейнере. Для этого используйте `docker run` команду `-v <host directory>:/var/opt/mssql` с флагом. Это позволяет восстанавливать данные между выполнениями контейнеров.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

Этот метод также позволяет предоставлять общий доступ и просматривать файлы на узле за пределами DOCKER.

> [!IMPORTANT]
> Сопоставление томов узлов для DOCKER на Mac с образом SQL Server на Linux не поддерживается в настоящее время. Вместо этого используйте контейнеры томов данных. Это ограничение относится только к `/var/opt/mssql` каталогу. Чтение из подключенного каталога работает нормально. Например, можно подключить каталог узлов с помощью-v на Mac и восстановить резервную копию из файла BAK, находящегося на узле.

### <a name="use-data-volume-containers"></a>Использование контейнеров томов данных

Второй вариант — использовать контейнер томов данных. Вы можете создать контейнер томов данных, указав имя тома вместо каталога узлов с `-v` параметром. В следующем примере создается общий том данных с именем **склволуме**.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```
::: moniker-end

> [!NOTE]
> Этот метод неявного создания тома данных в команде Run не работает с более старыми версиями DOCKER. В этом случае используйте явные шаги, описанные в документации по DOCKER, [Создание и подключение контейнера тома данных](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Даже если вы останавливаете и удаляете этот контейнер, том данных сохраняется. Его можно просмотреть с помощью `docker volume ls` команды.

```bash
docker volume ls
```

Если затем создать другой контейнер с тем же именем тома, то новый контейнер будет использовать те же данные SQL Server данных, которые содержатся в томе.

Чтобы удалить контейнер тома данных, используйте `docker volume rm` команду.

> [!WARNING]
> Если удалить контейнер томов данных, все SQL Server данные в контейнере будут удалены *без возможности восстановления* .

### <a name="backup-and-restore"></a>Резервное копирование и восстановление

В дополнение к этим приемам контейнеров можно также использовать стандартные SQL Server методы резервного копирования и восстановления. Файлы резервной копии можно использовать для защиты данных или для перемещения данных в другой экземпляр SQL Server. Дополнительные сведения см. в статье [резервное копирование и восстановление SQL Server баз данных в Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> При создании резервных копий обязательно создайте или скопируйте файлы резервных копий за пределами контейнера. В противном случае, если контейнер удален, файлы резервных копий также будут удалены.

## <a name="execute-commands-in-a-container"></a>Выполнение команд в контейнере

При наличии работающего контейнера можно выполнять команды в контейнере из главного терминала.

Чтобы получить идентификатор контейнера, выполните следующие действия.

```bash
docker ps
```

Чтобы запустить терминал Bash в контейнере, выполните следующее:

```bash
docker exec -it <Container ID> /bin/bash
```

Теперь вы можете выполнять команды, как будто они выполняются в терминале внутри контейнера. По завершении введите `exit`. Это завершается в интерактивном сеансе команд, но контейнер продолжит работу.

## <a name="copy-files-from-a-container"></a>Копирование файлов из контейнера

Чтобы скопировать файл из контейнера, используйте следующую команду:

```bash
docker cp <Container ID>:<Container path> <host path>
```

**Пример.**

```bash
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog /tmp/errorlog
```

```PowerShell
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog C:\Temp\errorlog
```

## <a name="copy-files-into-a-container"></a>Копирование файлов в контейнер

Чтобы скопировать файл в контейнер, используйте следующую команду:

```bash
docker cp <Host path> <Container ID>:<Container path>
```

**Пример.**

```bash
docker cp /tmp/mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

```PowerShell
docker cp C:\Temp\mydb.mdf d6b75213ef80:/var/opt/mssql/data
```
## <a id="tz"></a>Настройка часового пояса

Чтобы запустить SQL Server в контейнере Linux с заданным часовым поясом, настройте переменную **окружения** . Чтобы найти правильное значение часового пояса, выполните команду **тзселект** в командной строке Linux Bash:

```bash
tzselect
```

После выбора часового пояса **тзселект** отображает выходные данные, аналогичные следующим:

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

Эти сведения можно использовать для задания одной и той же переменной среды в контейнере Linux. В следующем примере показано, как запустить SQL Server в контейнере в `Americas/Los_Angeles` часовом поясе:

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -p 1433:1433 --name sql1 \
   -e 'TZ=America/Los_Angeles'\
   -d mcr.microsoft.com/mssql/server:2017-latest 
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2017-latest 
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -p 1433:1433 --name sql1 \
   -e 'TZ=America/Los_Angeles'\
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```
::: moniker-end

## <a id="tags"></a>Запуск определенного образа контейнера SQL Server

Существуют сценарии, в которых может потребоваться не использовать последний SQL Server образ контейнера. Чтобы запустить конкретный образ контейнера SQL Server, выполните следующие действия.

1. Укажите **тег** DOCKER для выпуска, который вы хотите использовать. Чтобы просмотреть доступные теги, см. [страницу концентратора DOCKER для MSSQL-Server-Linux](https://hub.docker.com/_/microsoft-mssql-server).

2. Вытяните SQL Server образ контейнера с тегом. Например, чтобы извлечь образ RC1, замените `<image_tag>` в следующей `rc1`команде на.

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. Чтобы запустить новый контейнер с этим образом, укажите имя тега в `docker run` команде. В следующей команде замените `<image_tag>` версией, которую необходимо запустить.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

Эти шаги также можно использовать для понижения уровня существующего контейнера. Например, может потребоваться откатить или понизить уровень выполняющегося контейнера для устранения неполадок или тестирования. Чтобы перейти на более раннюю версию работающего контейнера, необходимо использовать метод сохраняемости для папки данных. Выполните те же действия, описанные в [разделе Обновление](#upgrade), но при запуске нового контейнера укажите имя тега более старой версии.

## <a id="version"></a>Проверка версии контейнера

Если вы хотите получить сведения о версии SQL Server в работающем контейнере DOCKER, выполните следующую команду, чтобы отобразить ее. Замените `<Container ID or name>` на идентификатор целевого контейнера или имя. Замените `<YourStrong!Passw0rd>` на SQL Server пароль для имени входа sa.

```bash
sudo docker exec -it <Container ID or name> /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourStrong!Passw0rd>' \
   -Q 'SELECT @@VERSION'
```

```PowerShell
docker exec -it <Container ID or name> /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourStrong!Passw0rd>" `
   -Q 'SELECT @@VERSION'
```

Кроме того, можно указать версию SQL Server и номер сборки для целевого образа контейнера DOCKER. Следующая команда отображает версию SQL Server и сведения о сборке для образа **Microsoft/MSSQL-Server-Linux: 2017-Latest** . Это достигается путем запуска нового контейнера с переменной среды **PAL_PROGRAM_INFO = 1**. Результирующий контейнер мгновенно завершает работу, и `docker rm` команда удаляет его.

```bash
sudo docker run -e PAL_PROGRAM_INFO=1 --name sqlver \
   -ti mcr.microsoft.com/mssql/server:2017-latest && \
   sudo docker rm sqlver
```

```PowerShell
docker run -e PAL_PROGRAM_INFO=1 --name sqlver `
   -ti mcr.microsoft.com/mssql/server:2017-latest; `
   docker rm sqlver
```

Предыдущие команды отображают сведения о версии, аналогичные приведенным ниже.

```Text
sqlservr
  Version 14.0.3029.16
  Build ID ee3d3882f1c48a7a7e590a620153012eaedc2f37143d485df945a079b9d4eeea
  Build Type release
  Git Version 65d42c4
  Built at Sat Jun 16 01:20:11 GMT 2018

PAL
  Build ID 60cfcb134bbae96d311f6a4f56aeb5a685b3809de80bcb61ec587a8f58b555eb
  Build Type release
  Git Version 21a4c11
  Built at Sat Jun 16 01:18:53 GMT 2018

Packages
  system.sfp                    6.2.9200.1,21a4c1178,
  system.common.sfp             10.0.15063.540
  system.certificates.sfp       6.2.9200.1,21a4c1178,
  system.netfx.sfp              4.6.1590.0
  secforwarderxplat.sfp         14.0.3029.16
  sqlservr.sfp                  14.0.3029.16
  sqlagent.sfp                  14.0.3029.16
```

## <a id="upgrade"></a>Обновление SQL Server в контейнерах

Чтобы обновить образ контейнера с помощью DOCKER, сначала найдите тег для выпуска обновления. Извлекать эту версию из реестра с помощью `docker pull` команды:

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

Это приведет к обновлению образа SQL Server для всех создаваемых вами контейнеров, но не будет обновлять SQL Server в любых выполняющихся контейнерах. Для этого необходимо создать новый контейнер с последним SQL Server образом контейнера и перенести данные в этот новый контейнер.

1. Убедитесь, что вы используете один из [методов сохраняемости данных](#persist) для существующего контейнера SQL Server. Это позволяет запустить новый контейнер с теми же данными.

1. Завершите работу контейнера SQL Server с `docker stop` помощью команды.

1. Создайте новый контейнер SQL Server с помощью `docker run` и укажите сопоставленный каталог узла или контейнер томов данных. Обязательно используйте конкретный тег для обновления SQL Server. Новый контейнер теперь использует новую версию SQL Server с существующими данными SQL Server.

   > [!IMPORTANT]
   > В настоящее время обновление поддерживается только между RC1, RC2 и общедоступной версией.

1. Проверьте свои базы данных и данные в новом контейнере.

1. При необходимости удалите старый контейнер с помощью `docker rm`.

## <a id="troubleshooting"></a> Устранение неполадок

В следующих разделах приведены рекомендации по устранению неполадок при выполнении SQL Server в контейнерах.

### <a name="docker-command-errors"></a>Ошибки команды DOCKER

При получении ошибок для любой `docker` команды убедитесь, что служба DOCKER запущена, и попробуйте запустить с повышенными разрешениями.

Например, в Linux при выполнении `docker` команд может появиться следующая ошибка:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Если вы получаете эту ошибку в Linux, попробуйте выполнить те же команды, которые предварялись `sudo`. Если это не удается, убедитесь, что служба DOCKER запущена, и при необходимости запустите ее.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

В Windows убедитесь, что вы запускаете PowerShell или командную строку от имени администратора.

### <a name="sql-server-container-startup-errors"></a>Ошибки при запуске контейнера SQL Server

Если не удается запустить контейнер SQL Server, попробуйте выполнить следующие тесты:

- Если возникает ошибка, например **"не удалось создать конечную точку CONTAINER_NAME в сетевом мосте. Ошибка запуска прокси-сервера: прослушивание TCP 0.0.0.0: привязка 1433: адрес уже используется.** , вы пытаетесь сопоставлять порт контейнера 1433 с уже используемым портом. Это может произойти, если вы используете SQL Server локально на размещающем компьютере. Это также может произойти, если запустить два контейнера SQL Server и попытаться сопоставлять их с одним и тем же портом узла. В этом случае используйте `-p` параметр, чтобы связать порт контейнера 1433 с другим портом узла. Пример: 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2017-latest`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2017-latest`.
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu`.
```

::: moniker-end

- Если при попытке подключения к сокету управляющей программы DOCKER по адресу UNIX:///var/run/DOCKER.sock появляется сообщение об ошибке, **например "отказано в разрешении": Получить http://%2Fvar%2Frun%2Fdocker.sock/v1.30tdout=1&tail=all: доступ к UNIX/Вар/рун/доккер.Сокк: Connect:** отказано в разрешении при попытке запустить контейнер, а затем добавить пользователя в группу DOCKER в Ubuntu. Затем выйдите из системы и войдите снова, так как это изменение повлияет на новые сеансы. 

   ```bash
    usermod -aG docker $USER
    ```
- Проверьте наличие сообщений об ошибках из контейнера.

    ```bash
    docker logs e69e056c702d
    ```

- Убедитесь, что вы отвечаете минимальным требованиям к объему памяти и диску, указанным в разделе [Предварительные требования](quickstart-install-connect-docker.md#requirements) статьи краткое руководство.

- Если вы используете программное обеспечение для управления контейнерами, убедитесь, что оно поддерживает процессы контейнеров, работающие в качестве привилегированных. Процесс Sqlservr в контейнере выполняется как root.

- Проверьте [настройки SQL Server и журналы ошибок](#errorlogs).

### <a name="enable-dump-captures"></a>Включение захвата дампа

В случае сбоя SQL Server процесса в контейнере необходимо создать новый контейнер с включенным **SYS_PTRACE** . Это добавляет возможность использования Linux для трассировки процесса, который необходим для создания файла дампа при возникновении исключения. Файл дампа может использоваться поддержкой для устранения проблемы. Эта возможность включает Следующая команда DOCKER Run.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>Ошибки подключения SQL Server

Если вы не можете подключиться к экземпляру SQL Server, работающему в контейнере, попробуйте выполнить следующие тесты:

- Убедитесь, что контейнер SQL Server работает, просмотрев столбец `docker ps -a` **состояние** выходных данных. В противном случае `docker start <Container ID>` используйте для запуска.

- Если вы сопоставили порт узла, отличный от порта по умолчанию (не 1433), убедитесь, что вы указываете порт в строке подключения. Сопоставление портов можно увидеть в столбце Ports ( **порты** ) `docker ps -a` выходных данных. Например, следующая команда подключает sqlcmd к контейнеру, слушающему порт 1401:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Если используется `docker run` с существующим сопоставленным томом данных или контейнером томов данных, SQL Server игнорирует `MSSQL_SA_PASSWORD`значение. Вместо этого предварительно настроенный пароль пользователя SA используется из данных SQL Server в томе данных или в контейнере томов данных. Убедитесь, что вы используете пароль SA, связанный с данными, к которым вы подключаетесь.

- Проверьте [настройки SQL Server и журналы ошибок](#errorlogs).

### <a name="sql-server-availability-groups"></a>SQL Server группы доступности

Если вы используете DOCKER с группами доступности SQL Server, есть два дополнительных требования.

- Сопоставьте порт, используемый для связи с репликой (по умолчанию 5022). Например, укажите `-p 5022:5022` в качестве части `docker run` команды.

- Явно задайте имя узла контейнера с помощью `-h YOURHOSTNAME` параметра `docker run` команды. Это имя узла используется при настройке группы доступности. Если вы не укажете его `-h`с помощью, по умолчанию используется идентификатор контейнера.

### <a id="errorlogs"></a>SQL Server установки и журналы ошибок

Вы можете просмотреть SQL Server установки и журналы ошибок в **/var/opt/MSSQL/log**. Если контейнер не запущен, сначала запустите контейнер. Затем используйте интерактивную командную строку для проверки журналов.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

Из сеанса Bash в контейнере выполните следующие команды:

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Если вы установили каталог узла для **/Вар/ОПТ/мсскл** при создании контейнера, то можете просмотреть подкаталог **log** на сопоставленном пути на узле.

## <a name="next-steps"></a>Следующие шаги

Начните работу с образами контейнеров SQL Server 2017 в DOCKER, выполнив инструкции в [кратком руководстве](quickstart-install-connect-docker.md).

Кроме того, см. Дополнительные сведения о ресурсах, отзывах и известных проблемах в [репозитории MSSQL-DOCKER GitHub](https://github.com/Microsoft/mssql-docker) .

[Изучение высокого уровня доступности для SQL Server контейнеров](sql-server-linux-container-ha-overview.md)
