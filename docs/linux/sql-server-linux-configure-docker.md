---
title: Параметры конфигурации для SQL Server в Docker | Документация Майкрософт
description: Ознакомьтесь с различными способами с помощью и взаимодействия с SQL Server 2017 и 2019 изображения предварительного просмотра контейнера в Docker. Сюда входят сохранение данных, копирование файлов и устранения неполадок.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: f6364755ee1719a17f4927cfd157b757c6097830
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705554"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Настройка образов контейнеров SQL Server в Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье объясняется, как настроить и использовать [образ контейнера mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) с помощью Docker. Этот образ содержит SQL Server, работающий в системе Linux, основанной на Ubuntu 16.04. Он может использоваться с Dосker Engine 1.8+ на Linux или Docker для Mac или Windows.

> [!NOTE]
> Эта статья посвящена специально с использованием образа mssql-server-linux. Образ Windows не рассматривается, но Дополнительные сведения о нем на [странице Docker Hub mssql-server-windows](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a name="pull-and-run-the-container-image"></a>Извлечение и запуск образа контейнера

Для извлечения и запуска Docker образов контейнеров для предварительной версии SQL Server 2017 и SQL Server 2019, выполните предварительные требования и шаги в следующем кратком руководстве.

- [Запустите образ контейнера SQL Server 2017 с Docker](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Запустите образ контейнера SQL Server 2019 предварительной версии с помощью Docker](quickstart-install-connect-docker.md?view=sql-server-ver15)

В этой статье конфигурации содержит избыточное использование сценариев, в следующих разделах.

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a> Запуск образов контейнеров на основе RHEL

Вся документация об образах контейнеров SQL Server Linux укажите контейнеры на основе Ubuntu. Начиная с предварительной версией SQL Server 2019, можно использовать контейнеры на основе по Red Hat Enterprise Linux (RHEL). Изменения в репозитории контейнера из **mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu** для **mcr.microsoft.com/mssql/rhel/server:2019-CTP2.4** во всех команд docker.

Например следующая команда извлекает последний контейнер предварительной версии SQL Server 2019, использующий RHEL:

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP2.4
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP2.4
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a> Запуске производственных образов контейнера

Краткое руководство, в предыдущем разделе выполняется разработчика бесплатная версия SQL Server из Docker Hub. Большая часть информации по-прежнему применяется, если вы хотите запуске производственных образов контейнера, например выпуски Enterprise, Standard или Web. Тем не менее существует ряд различий, которые здесь описаны.

- SQL Server в рабочей среде можно использовать, только если у вас есть действительная лицензия. Можно получить бесплатную лицензию SQL Server Express рабочей [здесь](https://go.microsoft.com/fwlink/?linkid=857693). Лицензии SQL Server Standard и Enterprise Edition можно приобрести [корпоративного лицензирования Майкрософт](https://www.microsoft.com/licensing/default.aspx).


- Образ контейнера разработчика можно настроить для запуска в рабочей среде выпусках. Следуйте инструкциям ниже для запуска производственными выпусками:

Ознакомьтесь с требованиями и выполните процедуры [быстрого запуска](quickstart-install-connect-docker.md). Необходимо указать производственного выпуска с **MSSQL_PID** переменной среды. Приведенный ниже показано, как запустить последний образ контейнера SQL Server 2017 для выпуска Enterprise Edition:

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
> Путем передачи значения **Y** в переменную среды **ACCEPT_EULA** и значение edition **MSSQL_PID**, вы выражаете наличие допустимым и существующие лицензии выпуск и версия SQL Server, который вы собираетесь использовать. Кроме того, вы соглашаетесь, что использование программного обеспечения SQL Server, работающих в образ контейнера Docker, подпадают под условия лицензии SQL Server.

> [!NOTE]
> Полный список возможных значений для **MSSQL_PID**, см. в разделе [параметры SQL Server можно настроить с помощью переменных среды в Linux](sql-server-linux-configure-environment-variables.md).

::: moniker-end

## <a name="connect-and-query"></a>Подключение и запрос

Подключение и запрос SQL Server в контейнере с либо вне контейнера или в контейнере. Ниже описаны оба сценария. 

### <a name="tools-outside-the-container"></a>Средства вне контейнера

Подключении к экземпляру SQL Server на компьютере Docker с помощью любого внешнего инструмента macOS, Windows или Linux, поддерживающего подключения SQL. Некоторые стандартные средства включают:

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md);
- [SQL Server Management Studio (SSMS) в Windows](sql-server-linux-manage-ssms.md);

В следующем примере используется **sqlcmd** для подключения к SQL Server, запущенный в контейнере Docker. IP-адрес в строке подключения — это IP-адрес хост-компьютера, на котором выполняется контейнер.

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

Был сопоставлен с портом узла, не по умолчанию **1433**, добавьте этот порт в строке подключения. Например, если вы указали `-p 1400:1433` в вашей `docker run` команды, а затем соедините с явным образом указать порт 1400.

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>Инструменты в контейнере

Начиная с SQL Server 2017 preview, [средств командной строки SQL Server](sql-server-linux-setup-tools.md) включены в образ контейнера. При подключении к образу с интерактивной командной строке средства можно запустить локально.

1. Выполните команду `docker exec -it`, чтобы запустить интерактивную оболочку bash внутри запущенного контейнера. В следующем примере `e69e056c702d` идентификатор контейнера.

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > Не всегда нужно указать идентификатор весь контейнер. Необходимо только указать достаточного количества символов для уникальной идентификации. То есть в данном случае это будет достаточно, чтобы использовать `e6` или `e69` вместо того чтобы полный идентификатор.

2. После входа в контейнер подключитесь локально с помощью sqlcmd. Обратите внимание, что sqlcmd не в пути по умолчанию, поэтому вам нужно будет указать полный путь.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. После завершения с помощью sqlcmd, введите `exit`.

4. Закончив работу с интерактивной командной строке, введите `exit`. Контейнер продолжит работать после выхода из интерактивной оболочки bash.

## <a name="run-multiple-sql-server-containers"></a>Запуск нескольких контейнеров SQL Server

Docker позволяет выполнять несколько контейнеров SQL Server на одном хост-компьютере. Этот подход для сценариев, требующих несколько экземпляров SQL Server на одном узле. Каждый контейнер должен представляться в другом порте.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

В следующем примере создаются два контейнера SQL Server 2017 и сопоставляет их с порты **1401** и **1402** на хост-компьютере.

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

В следующем примере создаются два контейнера предварительной версии SQL Server 2019 и сопоставляет их с порты **1401** и **1402** на хост-компьютере.

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

::: moniker-end

Теперь существуют два экземпляра SQL Server выполняется в отдельном контейнере. Клиенты могут подключаться к каждому экземпляру SQL Server с помощью IP-адрес узла Docker и номер порта для контейнера.

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a> Создать настраиваемый контейнер

Можно создать свой собственный [Dockerfile](https://docs.docker.com/engine/reference/builder/#usage) создать настраиваемый контейнер SQL Server. Дополнительные сведения см. в разделе [демонстрационный ролик, сочетает в себе SQL Server и приложение Node](https://github.com/twright-msft/mssql-node-docker-demo-app). При создании собственных Dockerfile, имейте в виду процесса переднего плана, так как этот процесс контролирует существования контейнера. Если он существует, контейнер завершит работу. Например если вы хотите запустить сценарий и запустите SQL Server, убедитесь, что процесс SQL Server — это команда крайнее правое. Все команды выполняются в фоновом режиме. Это продемонстрировано в следующую команду в Dockerfile.

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

Если вы в обратном порядке команды в предыдущем примере, контейнер будет завершить работу после завершения сценария my-sql-commands.sh.

## <a id="persist"></a> Сохранить данные

Изменения конфигурации SQL Server и файлов базы данных сохраняются в контейнере даже при перезагрузке в контейнере с `docker stop` и `docker start`. Тем не менее если удалить контейнер с `docker rm`, все данные в контейнере удаляются, включая SQL Server и баз данных. Следующий раздел объясняет, как использовать **тома данных** для хранения файлов базы данных, даже если будут удалены связанные контейнеры.

> [!IMPORTANT]
> Для SQL Server очень важно, что вы понимаете постоянного хранения в Docker. В дополнение к обсуждение в этом разделе, см. в разделе документации Docker на [управление данными в контейнерах Docker](https://docs.docker.com/engine/tutorials/dockervolumes/).

### <a name="mount-a-host-directory-as-data-volume"></a>Подключить каталог узла в качестве тома данных

Первый способ — подключение к каталогу на узле в качестве тома данных в контейнере. Чтобы сделать это, используйте `docker run` с `-v <host directory>:/var/opt/mssql` флаг. Благодаря этому данные для восстановления между выполнениями контейнера.

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

::: moniker-end

Этот метод также позволяет совместно использовать и просматривать файлы на узле за пределами Docker.

> [!IMPORTANT]
> Сопоставление томов узла для Docker на компьютере Mac с SQL Server в образе Linux не поддерживается в настоящее время. Вместо этого используйте контейнеры томов данных. Это ограничение относится только к `/var/opt/mssql` каталога. Чтение из подключенного каталога работает нормально. Например можно подключить узел каталога, используя - v на компьютере Mac и восстановить резервную копию из BAK-файле, который находится на узле.

### <a name="use-data-volume-containers"></a>Используйте контейнеры томов данных

Второй вариант — использовать контейнер томов данных. Можно создать контейнер томов данных, указав имя тома вместо каталога узла с `-v` параметра. В следующем примере создается общего тома данных с именем **sqlvolume**.

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```
::: moniker-end

> [!NOTE]
> Этот метод для неявного создания тома данных в команду выполнения не работает с более старыми версиями Docker. В этом случае следует использовать явное действия, описанные в документации по Docker [Создание и подключение контейнера томов данных](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container).

Даже в том случае, если остановить и удалить этот контейнер, объем данных будет повторяться. Вы можете просмотреть ее с `docker volume ls` команды.

```bash
docker volume ls
```

Если затем создать другой контейнер с тем же именем тома, новый контейнер используются те же данные SQL Server, находящиеся на томе.

Чтобы удалить контейнер томов данных, используйте `docker volume rm` команды.

> [!WARNING]
> Если удалить контейнер томов данных, все данные SQL Server в контейнере, *окончательно* удалены.

### <a name="backup-and-restore"></a>Резервное копирование и восстановление

Помимо этих методов контейнера можно также использовать стандартную резервную копию SQL Server и восстановить методы. Файлы резервных копий можно использовать для защиты данных или для перемещения данных на другой экземпляр SQL Server. Дополнительные сведения см. в разделе [резервное копирование и восстановление баз данных SQL Server в Linux](sql-server-linux-backup-and-restore-database.md).

> [!WARNING]
> При создании резервных копий, убедитесь, что для создания или скопируйте файлы резервной копии вне контейнера. В противном случае при удалении контейнера также удаляются файлы резервной копии.

## <a name="execute-commands-in-a-container"></a>Выполнение команд в контейнере

При наличии запущенном контейнере, можно выполнять команды в контейнере с терминала узла.

Чтобы получить идентификатор контейнера выполните:

```bash
docker ps
```

Запуск bash, терминала в запустить контейнер:

```bash
docker exec -ti <Container ID> /bin/bash
```

Теперь можно выполнять команды, как если бы, если вы используете их в окне терминала внутри контейнера. По завершении введите `exit`. Это завершает работу в сеансе интерактивной командой, но продолжит работу вашего контейнера.

## <a name="copy-files-from-a-container"></a>Скопируйте файлы из контейнера

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

## <a name="copy-files-into-a-container"></a>Скопируйте файлы в контейнер

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
## <a id="tz"></a> Настройте часовой пояс

Для запуска SQL Server в контейнере Linux с помощью определенного часового пояса, настроить **TZ** переменной среды. Чтобы найти значения правого часового пояса, выполните **tzselect** команду из командной строки Linux bash:

```bash
tzselect
```

После выбора часового пояса, **tzselect** отображает выходные данные следующего вида:

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

Эти сведения можно использовать для задания одной переменной среды в контейнере Linux. В следующем примере показано, как для запуска SQL Server в контейнере в `Americas/Los_Angeles` часовой пояс:

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
   -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```
::: moniker-end

## <a id="tags"></a> Запуск определенного образа контейнера SQL Server

Существуют сценарии, где может потребоваться использовать последний образ контейнера SQL Server. Для запуска определенного образа контейнера SQL Server, следуйте инструкциям ниже:

1. Определить Docker **тега** к выпуску, вы хотите использовать. Чтобы просмотреть доступные теги, см. в разделе [соответствующая страница концентратора Docker mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server).

2. Получите образ контейнера SQL Server с тегом. Например, чтобы извлечь образ RC1, замените `<image_tag>` в следующей команде с `rc1`.

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. Чтобы запустить новый контейнер с помощью этого образа, укажите имя тега в `docker run` команды. В следующей команде замените `<image_tag>` с версией, будут выполняться.

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

Эти действия можно также понизить существующий контейнер. Например вы хотите выполнить откат или понизить запущенном контейнере для устранения неполадок или тестирования. Чтобы понизить запущенному контейнеру, необходимо использовать метод постоянного хранения для папки данных. Выполните те же действия, описанные в [обновить раздел](#upgrade), но укажите имя тега для более ранней версии, при запуске нового контейнера.

## <a id="version"></a> Проверьте версию контейнера

Если вы хотите узнать версию SQL Server в запущенном контейнере docker, выполните следующую команду, чтобы отобразить ее. Замените `<Container ID or name>` с целевом контейнере с Идентификатором или именем. Замените `<YourStrong!Passw0rd>` с пароль для имени входа SA SQL Server.

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

Можно также определить версию SQL Server и номер сборки для целевой образ контейнера docker. Следующая команда отображает данные SQL Server версии и сборке для **microsoft/mssql-server-linux:2017-последние** изображения. Это достигается путем выполнения новый контейнер с помощью переменной среды **PAL_PROGRAM_INFO = 1**. Полученный контейнер сразу же завершает работу и `docker rm` команда удаляет его.

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

Приведенные выше команды для отображения сведений о версии, аналогичный приведенному ниже:

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

Обновление образа контейнера с помощью Docker, сначала найдите тег для выпуска для обновления. Извлечь из реестра с помощью этой версии `docker pull` команды:

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

Это обновляет образ SQL Server для любой новые контейнеры, созданные, но не приводит к обновлению SQL Server в любой запущенных контейнеров. Чтобы сделать это, необходимо создать контейнер с последний образ контейнера SQL Server и перенести данные в этот новый контейнер.

1. Убедитесь, что вы используете один из [методы сохраняемости данных](#persist) для существующего контейнера SQL Server. Это позволяет запустить новый контейнер с теми же данными.

1. Остановить контейнер SQL Server с помощью `docker stop` команды.

1. Создать новый контейнер SQL Server с `docker run` и укажите каталог сопоставленные узла или контейнер томов данных. Убедитесь в том, что для использования определенного тега для обновления SQL Server. Теперь новый контейнер использует новую версию SQL Server с помощью существующих данных SQL Server.

   > [!IMPORTANT]
   > Обновление поддерживается только между RC1 и RC2, общедоступной версии в настоящее время.

1. Проверка баз данных и данных в новый контейнер.

1. При необходимости удалите старый контейнер с `docker rm`.

## <a id="troubleshooting"></a> Устранение неполадок

Следующие разделы содержат сведения об устранении неполадок для запуска SQL Server в контейнерах.

### <a name="docker-command-errors"></a>Ошибки команды docker

Если возникают ошибки для любого `docker` команды, убедитесь, что служба docker запущена и попробуйте выполнить с повышенным уровнем разрешений.

Например, в Linux, может появиться следующая ошибка при выполнении `docker` команды:

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Если вы получаете эту ошибку в Linux, попробуйте выполнить те же команды, имя которого начинается с `sudo`. В случае неудачи убедитесь служба docker запущена и запустите ее при необходимости.

```bash
sudo systemctl status docker
sudo systemctl start docker
```

В Windows убедитесь, что вы запускаете PowerShell или командной строке с правами администратора.

### <a name="sql-server-container-startup-errors"></a>Ошибки при запуске контейнера SQL Server

Если контейнер SQL Server не удается выполнить, попробуйте выполните следующие тесты:

- Если отобразится сообщение об ошибке **"не удалось создать конечную точку CONTAINER_NAME на сетевой мост. Ошибка при запуске прокси-сервера: прослушивания tcp 0.0.0.0:1433 привязки: адрес уже используется. "** , а затем вы пытаетесь сопоставления контейнера с портом 1433 в порт, который уже используется. Это может произойти, если вы используете SQL Server локально на хост-компьютере. Это также может произойти, если вы запустите два контейнера SQL Server и сопоставьте их обе на один и тот же порт узла. В этом случае используйте `-p` параметр для сопоставления с другой узел порт контейнера с портом 1433. Пример: 

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu`.
```

::: moniker-end

- Установите этот флажок, чтобы определить наличие сообщения об ошибках из контейнера.

    ```bash
    docker logs e69e056c702d
    ```

- Убедитесь, что вы минимальным требованиям к памяти и диска указан в [предварительные требования](quickstart-install-connect-docker.md#requirements) статьи краткого руководства.

- Если вы используете программное обеспечение управления контейнеров, убедитесь, что он поддерживает контейнера, запущенного в качестве привилегированного пользователя. Процесс sqlservr в контейнере работает как корень.

- Просмотрите [SQL Server программа установки и журналы ошибок](#errorlogs).

### <a name="enable-dump-captures"></a>Включить захват дампа

Если произошел сбой процесса SQL Server в контейнере, необходимо создать новый контейнер с **SYS_PTRACE** включена. Это добавляет Linux возможность трассировки процесс, который требуется для создания файла дампа при возникновении исключения. Файл дампа можно использоваться службой поддержки для устранения проблемы. Следующие команды docker run включающий эту возможность.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>Ошибки подключения SQL Server

Если не удается подключиться к SQL Server, работающий в контейнере, попробуйте выполните следующие тесты:

- Убедитесь, что контейнер SQL Server работает, просмотрев **состояние** столбец `docker ps -a` выходных данных. Если это не так, используйте `docker start <Container ID>` для его запуска.

- Если вы сопоставлен с портом узла не по умолчанию (не 1433), убедитесь, что порт указываются в строке подключения. Вы увидите сопоставление порта на **ПОРТЫ** столбец `docker ps -a` выходных данных. Например следующая команда устанавливает подключение sqlcmd в контейнер, который прослушивает порт 1401:

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- Если вы использовали `docker run` с существующего тома сопоставленные данные или контейнер томов данных, SQL Server пропускает значения `MSSQL_SA_PASSWORD`. Вместо этого используется предварительно заданный пароль пользователя SA, из данных SQL Server в объема данных или контейнер томов данных. Убедитесь, что вы используете пароль SA, связанный с данными, которые вы подключаете к.

- Просмотрите [SQL Server программа установки и журналы ошибок](#errorlogs).

### <a name="sql-server-availability-groups"></a>Группы доступности SQL Server

Если вы используете Docker с группами доступности SQL Server, существуют две дополнительные требования.

- Сопоставьте порт, который используется для обмена данными реплики (по умолчанию 5022). Например, указать `-p 5022:5022` как часть вашего `docker run` команды.

- Явно задать имя узла контейнера с `-h YOURHOSTNAME` параметр `docker run` команды. Это имя узла используется при настройке группы доступности. Если не указать его с `-h`, по умолчанию используется идентификатор контейнера.

### <a id="errorlogs"></a> SQL Server программа установки и журналы ошибок

Вы можете изучить работы программы установки SQL Server и журналы ошибок **/var/opt/mssql/log**. Если контейнер не выполняется, сначала запустите контейнер. Затем можно используйте интерактивной командной строки для изучения журналов.

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
> Если подключить каталог узла для **/var/opt/mssql** при создании контейнера, можно вместо этого меню **журнала** подкаталог на сопоставленный путь на узле.

## <a name="next-steps"></a>Следующие шаги

Начало работы с образами контейнеров SQL Server 2017 в Docker через [быстрого запуска](quickstart-install-connect-docker.md).

Кроме того, см. в разделе [репозиторий GitHub mssql-docker](https://github.com/Microsoft/mssql-docker) для ресурсов, отзывы и известные проблемы.

[Изучите высокий уровень доступности для контейнеров SQL Server](sql-server-linux-container-ha-overview.md)
