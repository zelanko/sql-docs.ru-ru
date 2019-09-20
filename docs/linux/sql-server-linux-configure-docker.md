---
title: Параметры конфигурации SQL Server в Docker
description: Различные способы использования образов контейнеров с SQL Server 2017 и 2019 (предварительная версия), а также взаимодействия с ними в Docker. Здесь вы найдете информацию о сохранении данных, копировании файлов и устранении неполадок.
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: c70ba17073030f4fbbe4851fffb84a4c4a30fbbc
ms.sourcegitcommit: da8bb7abd256b2bebee7852dc0164171eeff11be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988142"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Настройка образов контейнеров с SQL Server в Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка [образа контейнера mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) и его использование в Docker. Этот образ содержит SQL Server, работающий в системе Linux, основанной на Ubuntu 16.04. Он может использоваться с Dосker Engine 1.8+ на Linux или Docker для Mac или Windows.

> [!NOTE]
> В этой статье особое внимание уделяется использованию образа mssql-server-linux. Образ с Windows не рассматривается, но сведения о нем вы можете найти на странице [mssql-server-windows](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) центра Docker Hub.

## <a name="pull-and-run-the-container-image"></a>Извлечение и запуск образа контейнера

Для извлечения и запуска образов контейнеров Docker для SQL Server 2017 и SQL Server 2019 (предварительная версия) необходимо выполнить предварительные требования и действия, описываемые в следующем кратком руководстве:

- [Запуск образа контейнера с SQL Server 2017 в Docker](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Запуск образа контейнера с SQL Server 2019 (предварительная версия) в Docker](quickstart-install-connect-docker.md?view=sql-server-ver15)

Эта статья посвящена настройке и содержит дополнительные сценарии использования, описываемые в следующих разделах.

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a> Запуск образов контейнеров на основе RHEL

Вся документация по образам контейнеров с Linux для SQL Server содержит информацию о контейнерах на основе Ubuntu. Начиная с предварительной версии SQL Server 2019 вы можете использовать контейнеры на основе Red Hat Enterprise Linux (RHEL). Во всех командах Docker измените репозиторий контейнера с **mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu** на **mcr.microsoft.com/mssql/rhel/server:2019-CTP3.2**.

Например, следующая команда извлекает последнюю версию контейнера с SQL Server 2019 (предварительная версия), в которой используется RHEL:

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.2
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.2
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a> Запуск рабочих образов контейнера

В упомянутом в предыдущем разделе кратком руководстве используется бесплатный выпуск SQL Server Developer из центра Docker Hub. Основная часть приведенных здесь сведений также применима для использования рабочих образов контейнеров, таких как выпуски Enterprise, Standard или Web. Однако между ними есть несколько различий, которые будут описываться отдельно.

- Для использования SQL Server в рабочей среде вам потребуется действительная лицензия. Чтобы получить бесплатную рабочую лицензию SQL Server Express, воспользуйтесь [этой ссылкой](https://go.microsoft.com/fwlink/?linkid=857693). Лицензии SQL Server Standard и Enterprise доступны в рамках [программы корпоративного лицензирования Майкрософт](https://www.microsoft.com/licensing/default.aspx).


- Образ контейнера с выпуском Developer при необходимости можно настроить для запуска в рабочей среде. Для запуска рабочих выпусков выполните следующие действия:

Ознакомьтесь с требованиями и выполните процедуры, описываемые в [кратком руководстве](quickstart-install-connect-docker.md). Укажите рабочий выпуск с помощью переменной среды **MSSQL_PID**. В следующем примере показано, как запустить последнюю версию образа контейнера с SQL Server 2017 для выпуска Enterprise:

```bash
docker run --name sqlenterprise \
      -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -e 'MSSQL_PID=Enterprise' -p 1433:1433 \
      -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run --name sqlenterprise `
      -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -e "MSSQL_PID=Enterprise" -p 1433:1433 `
      -d "mcr.microsoft.com/mssql/server:2017-latest"
 ```

> [!IMPORTANT]
> Передавая значение **Y** в переменной среды **ACCEPT_EULA** и значение выпуска в переменной среды **MSSQL_PID**, вы подтверждаете, что у вас есть действительная лицензия на выпуск и версию SQL Server, которые вы хотите использовать. Кроме того, вы соглашаетесь с тем, что использование программного обеспечения SQL Server, выполняющегося в образе контейнера Docker, будет регламентироваться условиями вашей лицензии SQL Server.

> [!NOTE]
> Полный список поддерживаемых значений переменной **MSSQL_PID** см. в статье [Настройка параметров SQL Server с помощью переменных среды в Linux](sql-server-linux-configure-environment-variables.md).

::: moniker-end

## <a name="connect-and-query"></a>Подключение и выполнение запросов

Вы можете подключаться и выполнять запросы к SQL Server в контейнере как извне контейнера, так и внутри него. Оба эти сценария описываются в следующих разделах. 

### <a name="tools-outside-the-container"></a>Средства за пределами контейнера

Подключиться к экземпляру SQL Server на компьютере Docker можно с помощью любого внешнего инструмента в macOS, Windows или Linux, поддерживающего подключения SQL. Ниже перечислены некоторые распространенные средства:

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md);
- [SQL Server Management Studio (SSMS) в Windows](sql-server-linux-manage-ssms.md);

В следующем примере используется **sqlcmd** для подключения к SQL Server в контейнере Docker. IP-адрес в строке подключения соответствует IP-адресу хост-компьютера, на котором выполняется контейнер.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Если в сопоставлении используется отличный от заданного по умолчанию порт узла (**1433**), необходимо добавить этот порт в строку подключения. Например, если вы указали `-p 1400:1433` в команде `docker run`, для подключения необходимо явно указать порт 1400.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Средства внутри контейнера

Начиная с предварительной версии SQL Server 2017 [средства командной строки SQL](sql-server-linux-setup-tools.md) включены в образ контейнера. Если подключиться к образу с помощью интерактивной командной строки, можно запускать программы локально.

1. Выполните команду `docker exec -it`, чтобы запустить интерактивную оболочку bash внутри запущенного контейнера. В следующем примере `e69e056c702d` — это идентификатор контейнера.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Указывать идентификатор контейнера полностью во всех случаях не требуется. Достаточно указать количество символов, необходимое для его уникальной идентификации. Соответственно, вместо полного идентификатора в этом примере может использоваться форма `e6` или `e69`.

2. После входа в контейнер подключитесь локально с помощью sqlcmd. Обратите внимание, что средство sqlcmd не включено в путь по умолчанию, поэтому необходимо указать полный путь.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. По завершении работы с sqlcmd введите `exit`.

4. После завершения работы с интерактивной командной строкой введите `exit`. Контейнер продолжит работать после выхода из интерактивной оболочки bash.

## <a name="run-multiple-sql-server-containers"></a>Запуск нескольких контейнеров SQL Server

В Docker реализована возможность одновременно запускать несколько контейнеров SQL Server на одном хост-компьютере. Используйте этот подход в сценариях, когда на одном хост-компьютере требуется несколько экземпляров SQL Server. Каждый контейнер должен предоставляться через отдельный порт.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В следующем примере создаются два контейнера SQL Server 2017, которые сопоставляются с портами **1401** и **1402** на хост-компьютере.

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

В следующем примере создаются два контейнера SQL Server 2019 (предварительная версия), которые сопоставляются с портами **1401** и **1402** на хост-компьютере.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```

::: moniker-end

Обратите внимание, что в этом случае два экземпляра SQL Server будут выполняться в разных контейнерах. Клиенты могут подключаться к каждому из этих экземпляров SQL Server, указав IP-адрес узла Docker и номер порта для контейнера.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a> Создание настраиваемого контейнера

Для создания настраиваемого контейнера SQL Server вам потребуется собственный [Dockerfile](https://docs.docker.com/engine/reference/builder/#usage). Дополнительные сведения см. в [демонстрации совместной работы SQL Server и приложения Node](https://github.com/twright-msft/mssql-node-docker-demo-app). При создании Dockerfile обратите внимание на процесс переднего плана, который управляет жизненным циклом контейнера. В случае выхода из этого процесса контейнер будет закрыт. Например, если вы хотите выполнить скрипт и запустить SQL Server, процесс SQL Server должен указываться в команде в крайней правой позиции. Все остальные команды выполняются в фоновом режиме. Это демонстрируется на примере следующей команды в Dockerfile:

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

Если отменить команды в предыдущем примере, контейнер закроется после выполнения скрипта do-my-sql-commands.sh.

## <a id="persist"></a> Сохранение данных

Изменения в конфигурации SQL Server и файлы базы данных сохраняются в контейнере даже в том случае, если он был перезапущен с использованием команд `docker stop` и `docker start`. Тем не менее, если удалить контейнер с помощью команды `docker rm`, будет удалено все его содержимое, включая SQL Server и ваши базы данных. В следующем разделе описывается, как можно использовать **тома данных** для сохранения файлов базы данных даже в случае удаления связанных контейнеров.

> [!IMPORTANT]
> При работе с SQL Server крайне важно понимать принципы обеспечения сохраняемости данных в Docker. Помимо этого раздела, мы также рекомендуем вам ознакомиться с информацией об [управлении данными в контейнерах Docker](https://docs.docker.com/engine/tutorials/dockervolumes/) в документации по Docker.

### <a name="mount-a-host-directory-as-data-volume"></a>Подключение каталога узла в качестве тома данных

Первый способ состоит в подключении каталога на вашем узле в качестве тома данных для контейнера. Для этого используйте команду `docker run` с флагом `-v <host directory>:/var/opt/mssql`. Такой подход позволяет восстанавливать данные в перерывах между выполнениями контейнера.

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```

::: moniker-end

Кроме того, этот способ позволяет предоставлять общий доступ к файлам на узле и просматривать их за пределами Docker.

> [!IMPORTANT]
> На данный момент не поддерживается сопоставление томов узла для Docker на Mac с образом SQL Server на Linux. Вместо этого следует использовать контейнеры томов данных. Это ограничение относится только к каталогу `/var/opt/mssql`. Операции чтения из подключенного каталога осуществляются в нормальном режиме. Например, вы можете подключить каталог узла с помощью команды -v на Mac и восстановить резервную копию из файла с расширением BAK, который находится на узле.

### <a name="use-data-volume-containers"></a>Использование контейнеров томов данных

Второй способ подразумевает использование контейнеров томов данных. Чтобы создать контейнер тома данных, укажите имя тома вместо каталога узла с параметром `-v`. В следующем примере создается общий том данных с именем **sqlvolume**.

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```
::: moniker-end

> [!NOTE]
> Этот способ неявного создания тома данных в рамках команды выполнения не работает в старых версиях Docker. В таком случае следует явно выполнить действия, которые описываются в разделе [Создание и подключение контейнера тома данных](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) документации по Docker.

Даже если вы остановите и удалите этот контейнер, том данных будет сохранен. Вы сможете просмотреть его с помощью команды `docker volume ls`.

```bash
docker volume ls
```

Если затем создать другой контейнер с тем же именем тома, в новом контейнере будут использоваться данные SQL Server, располагающиеся на этом томе.

Чтобы удалить контейнер тома данных, воспользуйтесь командой `docker volume rm`.

> [!WARNING]
> Если вы удалите контейнер тома данных, все содержащиеся в нем данные SQL Server будут удалены *без возможности восстановления*.

### <a name="backup-and-restore"></a>Резервное копирование и восстановление

Помимо этих способов, вы также можете использовать стандартные методы резервного копирования и восстановления SQL Server. Резервные копии файлов можно использовать для защиты данных или их переноса на другой экземпляр SQL Server. Дополнительные сведения см. в статье [Резервное копирование и восстановление баз данных SQL Server на Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> Обратите внимание, что создаваемые резервные копии должны размещаться за пределами контейнера. В противном случае при удалении контейнера файлы резервных копий также будут удалены.

## <a name="execute-commands-in-a-container"></a>Выполнение команд в контейнере

Вы можете выполнять команды из работающего контейнера с помощью терминала узла.

Чтобы получить идентификатор контейнера, выполните следующую команду:

```bash
docker ps
```

Чтобы запустить терминал Bash в контейнере, выполните следующую команду:

```bash
docker exec -it <Container ID> /bin/bash
```

После этого вы можете выполнять команды так, как если бы они выполнялись из терминала внутри контейнера. По завершении введите `exit`. В этом случае завершается интерактивный сеанс команд, однако контейнер продолжает работать.

## <a name="copy-files-from-a-container"></a>Копирование файлов из контейнера

Чтобы скопировать файл из контейнера, выполните следующую команду:

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

Чтобы скопировать файл в контейнер, выполните следующую команду:

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
## <a id="tz"></a> Настройка часового пояса

Чтобы запустить SQL Server в контейнере Linux с определенным часовым поясом, настройте переменную среды `TZ`. Чтобы определить соответствующее значение часового пояса, выполните команду `tzselect` из командной строки Bash в Linux:

```bash
tzselect
```

После выбора часового пояса команда `tzselect` выводит данные примерно следующего вида:

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

Эти сведения можно использовать для установки соответствующей переменной среды в контейнере с Linux. В следующем примере демонстрируется, как запустить SQL Server в контейнере с часовым поясом `Americas/Los_Angeles`:

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
   -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```
::: moniker-end

## <a id="tags"></a> Запуск определенного образа контейнера с SQL Server

В некоторых сценариях не требуется использовать последнюю версию образа контейнера с SQL Server. Чтобы запустить определенный образ контейнера с SQL Server, выполните следующие действия:

1. Определите **тег** Docker для выпуска, который требуется использовать. Список всех доступных тегов см. на странице [mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) центра Docker Hub.

2. Извлеките образ контейнера с SQL Server по соответствующему тегу. Например, чтобы извлечь образ RC1, замените `<image_tag>` в следующей команде на `rc1`.

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. Чтобы запустить новый контейнер с этим образом, укажите название тега в команде `docker run`. В следующей команде замените `<image_tag>` на версию, которую требуется запустить.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

Эти действия также можно использовать для перехода на более раннюю версию существующего контейнера. Например, вы можете выполнить откат или перейти на более раннюю версию контейнера для устранения неполадок или тестирования. Чтобы перейти на более раннюю версию контейнера, необходимо использовать метод обеспечения сохраняемости для папки данных. Выполните действия, описываемые в разделе, посвященном [обновлению](#upgrade), однако при запуске контейнера укажите название тега, соответствующее более старой версии.

## <a id="version"></a> Проверка версии контейнера

Чтобы просмотреть версию SQL Server в запущенном контейнере Docker, выполните следующую команду. Замените `<Container ID or name>` на идентификатор или имя целевого контейнера. Замените `<YourStrong!Passw0rd>` на пароль SQL Server для имени входа системного администратора.

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

Также можно определить версию и номер сборки SQL Server для целевого образа контейнера Docker. Приведенная ниже команда выводит сведения о версии и номере сборки SQL Server для образа **mcr.microsoft.com/mssql/server:2017-latest**. Для этого запускается новый контейнер с переменной среды **PAL_PROGRAM_INFO=1**. Полученный контейнер моментально закрывается, а команда `docker rm` удаляет его.

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

При выполнении указанных выше команд возвращаются сведения о версии примерно следующего вида:

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

## <a id="upgrade"></a> Обновление SQL Server в контейнерах

Чтобы выполнить обновление образа контейнера Docker, сначала необходимо определить тег, соответствующий нужному выпуску. Чтобы извлечь эту версию из реестра, используйте команду `docker pull`:

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

При этом образ SQL Server будет обновлен только во вновь создаваемых контейнерах. В работающих контейнерах обновление не производится. Для этого необходимо создать новый контейнер с последней версией образа контейнера с SQL Server и перенести в него данные.

1. Убедитесь, что в отношении существующего контейнера с SQL Server применяется один из [методов обеспечения сохраняемости данных](#persist). Таким образом, вы можете запустить новый контейнер с теми же данными.

1. Остановите контейнер с SQL Server с помощью команды `docker stop`.

1. Создайте новый контейнер с SQL Server с помощью команды `docker run` и укажите сопоставленный каталог узла или контейнер тома данных. Обратите внимание на необходимость использовать тег, соответствующий обновлению SQL Server. В новом контейнере будет использоваться новая версия SQL Server с существующими данными SQL Server.

   > [!IMPORTANT]
   > На данный момент поддерживается обновление между версиями RC1, RC2 и общедоступной версией.

1. Убедитесь, что базы данных и данные перенесены в новый контейнер.

1. При необходимости удалите старый контейнер с помощью команды `docker rm`.

## <a id="troubleshooting"></a> Устранение неполадок

В следующих разделах приводятся рекомендации по устранению неполадок при выполнении SQL Server в контейнерах.

### <a name="docker-command-errors"></a>Ошибки команды Docker

Если вы получаете ошибки, связанные с командами `docker`, убедитесь, что служба Docker запущена, и попробуйте выполнить запуск с повышенными привилегиями.

Например, при выполнении команд `docker` в Linux вы можете получить следующее сообщение об ошибке:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Если вы получаете эту ошибку в Linux, попробуйте выполнить те же команды с префиксом `sudo`. Если этот способ также не сработает, убедитесь, что служба Docker запущена, и при необходимости запустите ее.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

В Windows убедитесь, что PowerShell или командная строка запущены от имени администратора.

### <a name="sql-server-container-startup-errors"></a>Ошибки при запуске контейнера с SQL Server

Если запуск контейнера SQL Server завершился сбоем, попробуйте выполнить следующие проверки:

- Если вы получаете ошибку вида **"Не удалось создать конечную точку CONTAINER_NAME в сетевом мосте. Ошибка запуска прокси-сервера: прослушивание tcp 0.0.0.0:1433 привязка: адрес уже используется"** , значит, предпринимается попытка выполнить сопоставление порта контейнера 1433 с портом, который уже используется. Это может произойти в том случае, если вы запускаете SQL Server локально на хост-компьютере. Кроме того, такая ситуация возможна при запуске двух контейнеров с SQL Server и попытке сопоставить их с одним портом узла. В этом случае используйте параметр `-p`, чтобы сопоставить порт контейнера 1433 с другим портом узла. Пример: 

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu`.
```

::: moniker-end

- Если вы получаете ошибку вида **"Отказано в получении разрешений при попытке подключиться к сокету управляющей программы Docker по адресу unix:///var/run/docker.sock: Получение http://%2Fvar%2Frun%2Fdocker.sock/v1.30tdout=1&tail=all: dial unix /var/run/docker.sock: подключение: отказано в разрешении"** при попытке запустить контейнер, добавьте своего пользователя в группу Docker в Ubuntu. После этого выйдите из системы и выполните вход снова, чтобы применить изменения к новым сеансам. 

   ```bash
    usermod -aG docker $USER
    ```
- Проверьте наличие сообщений об ошибках от контейнера.

    ```bash
    docker logs e69e056c702d
    ```

- Убедитесь, что ваша система отвечает требованиям к объему памяти и дисковому пространству, которые указаны в разделе [Предварительные требования](quickstart-install-connect-docker.md#requirements) статьи с кратким руководством.

- Если вы используете программное обеспечение для управления контейнером, убедитесь, что оно поддерживает привилегированное выполнение процессов контейнера. Процесс sqlservr в контейнере выполняется в привилегированном режиме.

- Проверьте [журналы установки и ошибок SQL Server](#errorlogs).

### <a name="enable-dump-captures"></a>Включение записи дампа

Если произошел сбой процесса SQL Server внутри контейнера, необходимо создать новый контейнер и включить для него **SYS_PTRACE**. При этом будет добавлена возможность отслеживания процесса в Linux, которая необходима для создания файла дампа при возникновении исключения. Файл дампа может использоваться службой поддержки в процессе устранения неполадок. Эту возможность можно включить с помощью следующей команды выполнения Docker.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>Сбой подключений SQL Server

Если вам не удается подключиться к экземпляру SQL Server, запущенному в контейнере, попробуйте выполнить следующие проверки:

- Убедитесь, что контейнер с SQL Server запущен. Для этого проверьте содержимое столбца **STATUS** (Состояние) в выходных данных команды `docker ps -a`. При необходимости запустите его с помощью команды `docker start <Container ID>`.

- Если в сопоставлении задан отличный от установленного по умолчанию (1433) порт узла, убедитесь, что порт указан в строке подключения. Сопоставление порта можно проверить в столбце **PORTS** (Порты) в выходных данных команды `docker ps -a`. Например, следующая команда подключает sqlcmd к контейнеру, прослушивающему порт 1401:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Если вы использовали `docker run` с существующим сопоставленным томом данных или контейнером тома данных, SQL Server игнорирует значение `MSSQL_SA_PASSWORD`. Вместо этого для тома данных или контейнера тома данных используется предварительно заданный пароль системного администратора, хранящийся в данных SQL Server. Убедитесь, что используемый пароль системного администратора связан с данными, к которым вы подключаетесь.

- Проверьте [журналы установки и ошибок SQL Server](#errorlogs).

### <a name="sql-server-availability-groups"></a>Группы доступности SQL Server

Если вы используете Docker с группами доступности SQL Server, существует два дополнительных требования.

- Выполните сопоставление порта, который используется для подключения к реплике (по умолчанию 5022). Например, укажите `-p 5022:5022` в команде `docker run`.

- Явно укажите имя узла контейнера с помощью параметра `-h YOURHOSTNAME` команды `docker run`. Это имя узла используется при настройке группы доступности. Если оно не задано с помощью команды `-h`, по умолчанию в этом качестве используется идентификатор контейнера.

### <a id="errorlogs"></a> Журналы установки и ошибок SQL Server

Вы можете просмотреть журналы установки и ошибок SQL Server в папке **/var/opt/mssql/log**. Если контейнер не запущен, сначала запустите его. Затем проверьте журналы с помощью интерактивной командной строки.

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

Из сеанса Bash внутри контейнера выполните следующие команды:

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> Если вы подключили каталог хоста к каталогу **/var/opt/mssql** при создании контейнера, вместо этого можно выполнять поиск в подкаталоге **log** по сопоставленному пути на узле.


## <a id="buildnonrootcontainer"></a> Сборка и запуск контейнеров SQL Server от имени непривилегированного пользователя

Чтобы создать контейнер SQL Server, который запускается от имени пользователя `mssql` (не являющегося привилегированным), выполните указанные ниже действия.

1. Скачайте [образец файла dockerfile для непривилегированного контейнера SQL Server](https://raw.githubusercontent.com/microsoft/mssql-docker/master/linux/preview/examples/mssql-server-linux-non-root/Dockerfile) и сохраните его как `dockerfile`.
 
2. Выполните следующую команду в контексте каталога dockerfile, чтобы выполнить сборку непривилегированного контейнера SQL Server:

```bash
cd <path to dockerfile>
docker build -t 2017-latest-non-root .
```
 
3. Запустите контейнер.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword@" --cap-add SYS_PTRACE --name sql1 -p 1433:1433 -d 2017-latest-non-root
```

> [!NOTE]
> Флаг `--cap-add SYS_PTRACE` необходим для создания дампов в целях устранения неполадок непривилегированных контейнеров SQL Server.
 
4. Убедитесь в том, что контейнер запущен от имени пользователя, не являющегося привилегированным:

Войдите в контейнер с помощью команды docker exec.
```bash
docker exec -it sql1 bash
```
 
Выполните команду `whoami`, которая вернет пользователя, от имени которого выполняется контейнер.
 
```bash
whoami
```
 

## <a id="nonrootuser"></a> Запуск контейнера от имени другого непривилегированного пользователя в узле

Чтобы запустить контейнер SQL Server от имени другого непривилегированного пользователя, добавьте флаг -u в команду docker run. Непривилегированный контейнер должен выполняться в составе привилегированной группы, если только том не подключен к каталогу /var/opt/mssql, к которому есть доступ у непривилегированного пользователя. Привилегированная группа не предоставляет дополнительных привилегированных разрешений пользователю, не являющемуся привилегированным.
 
**Выполнение от имени пользователя с ИД пользователя 4000**
 
SQL Server можно запускать с настраиваемым идентификатором пользователя. Например, следующая команда запускает SQL Server с идентификатором пользователя 4000:
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u 4000:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```
 
> [!Warning]
> Убедитесь в том, что в контейнере SQL Server есть именованный пользователь, например mssql или root. В противном случае SQLCMD невозможно будет запустить в контейнере. Вы можете проверить, выполняется ли контейнер SQL Server от имени именованного пользователя, запустив `whoami` в контейнере.

**Запуск непривилегированного контейнера от имени привилегированного пользователя**

При необходимости непривилегированный контейнер можно запустить от имени привилегированного пользователя. При этом контейнер также автоматически получает все разрешения на доступ к файлам.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" -u 0:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```
 
**Запуск от имени пользователя на хост-компьютере**
 
SQL Server можно запустить от имени существующего пользователя на хост-компьютере с помощью следующей команды:
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u $(id -u myusername):0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```
 
**Запуск от имени другого пользователя и группы**
 
SQL Server можно запускать от имени произвольного пользователя и группы. В этом примере подключенный том имеет разрешения, настроенные для пользователя или группы на хост-компьютере.
 
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u (id -u myusername):(id -g myusername) -v /path/to/mssql:/var/opt/mssql -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```
 
## <a id="storagepermissions"></a> Настройка разрешений на постоянное сохранение для непривилегированных контейнеров
Чтобы разрешить непривилегированному пользователю доступ к файлам базы данных в подключенных томах, пользователь или группа, от имени которых выполняется контейнер, должны иметь доступ к постоянному хранилищу файлов.  

Узнать текущего владельца файлов базы данных можно с помощью приведенной ниже команды.
 
```bash
ls -ll <database file dir>
```

Если у SQL Server нет доступа к сохраненным файлам базы данных, выполните одну из приведенных ниже команд.
 
 
**Предоставление привилегированной группе доступа к файлам базы данных для чтения и записи**

Предоставьте привилегированной группе разрешения на доступ к указанным ниже каталогам, чтобы у непривилегированного контейнера SQL Server был доступ к файлам базы данных.

```bash
chgroup -R 0 <database file dir>
chmod -R g=u <database file dir>
```
 
**Назначение непривилегированного пользователя владельцем файлов**

Это может быть непривилегированный пользователь по умолчанию или любой другой непривилегированный пользователь на ваш выбор. В этом примере в качестве непривилегированного пользователя задан пользователь с идентификатором 10001.

```bash
chown -R 10001:0 <database file dir>
```
 
## <a id="changefilelocation"></a> Изменение расположения файлов по умолчанию

Добавьте переменную `MSSQL_DATA_DIR`, чтобы изменить каталог данных в команде `docker run`, а затем подключите том к этому расположению, к которому имеет доступ пользователь контейнера.

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" -e "MSSQL_DATA_DIR=/my/file/path" -v /my/host/path:/my/file/path -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```


## <a name="next-steps"></a>Следующие шаги

Сведения о начале работы с образами контейнеров с SQL Server 2017 в Docker можно найти в [кратком руководстве](quickstart-install-connect-docker.md).

Кроме того, в репозитории GitHub [mssql-docker](https://github.com/Microsoft/mssql-docker) вы найдете полезные ресурсы, отзывы и информацию об известных проблемах.

[Обеспечение высокого уровня доступности для контейнеров SQL Server](sql-server-linux-container-ha-overview.md)
