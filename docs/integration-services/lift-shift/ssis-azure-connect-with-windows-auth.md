---
title: "Подключение к источникам данных и общим папкам с помощью проверки подлинности Windows | Microsoft Docs"
ms.date: 11/27/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b84fdd15fa4a6393b2350aaf75985653b6273f31
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authentication"></a>Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows
В этой статье описывается, как настроить каталог служб SQL Server Integration Services в базе данных SQL Azure для запуска пакетов, которые используют проверку подлинности Windows для подключения к локальным источникам данных и общим папкам Azure. С помощью проверки подлинности Windows можно подключаться к источникам данных в той же виртуальной сети, в которой размещена среда Azure SSIS Integration Runtime. Источники могут находиться в локальной среде, в виртуальных машинах Azure и в службе файлов Azure.

Учетные данные домена, указываемые при выполнении инструкций в этой статье, применяются ко всем операциям выполнения пакетов в экземпляре базы данных SQL, пока эти данные не будут изменены или удалены.

## <a name="provide-domain-credentials-for-windows-authentication"></a>Указание учетных данных домена для проверки подлинности Windows
Чтобы задать учетные данные домена, с помощью которых пакеты смогут подключаться к локальным источникам данных, используя проверку подлинности Windows, выполните указанные ниже действия.

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB). Дополнительные сведения см. в разделе [Подключение к базе данных каталога SSISDB в Azure](ssis-azure-connect-to-catalog-database.md).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните следующую хранимую процедуру и укажите соответствующие учетные данные домена:

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```

4.  Запустите пакеты служб SSIS. Пакеты используют предоставленные учетные данные для подключения к локальным источникам данных с помощью проверки подлинности Windows.

### <a name="view-domain-credentials"></a>Просмотр учетных данных домена
Чтобы просмотреть активные учетные данные домена, выполните указанные ниже действия.

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните следующую хранимую процедуру и просмотрите выходные данные:

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>Удаление учетных данных домена
Чтобы удалить учетные данные, заданные согласно инструкциям в этой статье, выполните указанные ниже действия.

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните следующую хранимую процедуру:

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-an-on-premises-sql-server"></a>Подключение к локальному серверу SQL Server
Чтобы проверить возможность подключения к локальному серверу SQL Server, выполните указанные ниже действия.

1.  Чтобы выполнить эту проверку, найдите компьютер, не присоединенный к домену.

2.  На не присоединенном к домену компьютере выполните следующую команду, чтобы запустить среду SQL Server Management Studio (SSMS) с требуемыми учетными данными домена:

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  В среде SSMS проверьте возможность подключения к требуемому локальному серверу SQL Server.

### <a name="prerequisites"></a>предварительные требования
Чтобы подключиться к локальному серверу SQL Server, используя пакет, запущенный в Azure, нужно включить следующие необходимые компоненты:

1.  В диспетчере конфигурации SQL Server включите протокол TCP/IP.
2.  Разрешите доступ с помощью брандмауэра Windows. Дополнительные сведения см. в статье [Configure the Windows Firewall to Allow SQL Server Access](https://docs.microsoft.com/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access) (Настройка брандмауэра Windows для разрешения доступа к SQL Server).
3.  Чтобы подключаться с использованием проверки подлинности Windows, убедитесь, что среда Integration Runtime для Azure-SSIS принадлежит к виртуальной сети, в которой также находится локальный сервер SQL Server.  Дополнительные сведения см. в разделе [Присоединение среды выполнения интеграции Azure SSIS к виртуальной сети](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network). Затем используйте `catalog.set_execution_credential`, чтобы указать учетные данные, как описано в этой статье.

## <a name="connect-to-an-on-premises-file-share"></a>Подключение к локальной общей папке
Чтобы проверить возможность подключения к локальной общей папке, выполните указанные ниже действия.

1.  Чтобы выполнить эту проверку, найдите компьютер, не присоединенный к домену.

2.  На компьютере, не присоединенном к домену, выполните приведенную ниже команду. Эта команда открывает окно командной строки с требуемыми учетными данными домена, а затем проверяет возможность подключения к общей папке, получая список каталогов.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Проверьте, возвращен ли список каталогов из локальной общей папки, которую необходимо использовать.

## <a name="connect-to-a-file-share-on-an-azure-vm"></a>Подключение к общей папке на виртуальной машине Azure
Чтобы подключиться к общей папке на виртуальной машине Azure, сделайте следующее:

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните хранимую процедуру `catalog.set_execution_credential`, как описано ниже.

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="connect-to-a-file-share-in-azure-files"></a>Подключение к общей папке в службе файлов Azure
Дополнительные сведения о файлах Azure см. в разделе [Файлы Azure](https://azure.microsoft.com/services/storage/files/).

Чтобы подключиться к общей папке в службе файлов Azure, сделайте следующее:

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните хранимую процедуру `catalog.set_execution_credential`, как описано ниже.

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Следующие шаги
- Разверните пакет. Дополнительные сведения см. в разделе [Развертывание проекта служб SSIS с помощью SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Запустите пакет. Дополнительные сведения см. в разделе [Выполнение пакета служб SSIS с помощью SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Создайте расписание для пакета. Дополнительные сведения см. в разделе [Планирование выполнения пакета служб SSIS в Azure](ssis-azure-schedule-packages.md).
