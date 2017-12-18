---
title: "Поддержка высокого уровня доступности в SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2202b61a9efce26edb0edcef53204351338ecee6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="scale-out-support-for-high-availability"></a>Поддержка высокого уровня доступности в Scale Out

В SSIS Scale Out высокий уровень доступности на стороне рабочей роли обеспечивается за счет выполнения пакетов с использованием нескольких рабочих ролей Scale Out.
Высокий уровень доступности на стороне мастера достигается за счет применения функций [AlwaysOn для каталога служб SSIS](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) и отказоустойчивого кластера Windows. Несколько экземпляров мастера Scale Out Master размещаются в отказоустойчивом кластере Windows. Если служба мастера Scale Out или SSISDB на основном узле отключены, служба или SSISDB на вторичном узле продолжают принимать запросы пользователей и взаимодействовать с рабочими ролями Scale Out. 

Чтобы настроить высокий уровень доступности на стороне мастера, выполните следующие действия.

## <a name="1-prerequisites"></a>1. Предварительные требования
Настроить отказоустойчивый кластер Windows. Инструкции см. в записи блога [Установка компонентов и средств отказоустойчивого кластера для Windows Server 2012)](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Installing the Failover Cluster Feature and Tools for Windows Server 2012). Компоненты и средства необходимо установить на всех узлах кластера.

## <a name="2-install-scale-out-master-on-primary-node"></a>2. Установка мастера Scale Out на основном узле
Установите службы ядра СУБД, службы интеграции и мастер Scale Out на основном узле для мастера Scale Out. 

Во время установки необходимо выполнить следующие действия. 
### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1. Настройте учетную запись домена в качестве учетной записи, с помощью которой выполняется служба мастера Scale Out.
Эта учетная запись должна впоследствии иметь доступ к SSISDB на вторичном узле в отказоустойчивом кластере Windows. Поскольку служба мастера Scale Out и SSISDB реализуют отдельную отработку отказа, они не могут находиться на одном узле.

![Конфигурация сервера высокой доступности](media/ha-server-config.PNG)

### <a name="22-include-scale-out-master-service-dns-host-name-in-the-cns-of-scale-out-master-certificate"></a>2.2. Включите имя узла DNS для службы мастера Scale Out в список CN для сертификата мастера Scale Out.

Это имя узла будет использоваться в конечной точке мастера Scale Out. 

![Конфигурация мастера высокой доступности](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-secondary-node"></a>3. Установка мастера Scale Out на вторичном узле
Установите службы ядра СУБД, службы интеграции и мастер Scale Out на вторичном узле для мастера Scale Out. 

Используйте тот же сертификат мастера Scale Out, что и на основном узле. Экспортируйте SSL-сертификат мастера Scale Out на основном узле с закрытым ключом и установите его в корневое хранилище сертификатов локального компьютера на вторичном узле. Выберите этот сертификат при установке мастера Scale Out.

![Конфигурация мастера высокой доступности 2](media/ha-master-config2.PNG)

> [!Note]
> Вы можете настроить несколько резервных мастеров Scale Out, повторив эти действия для вторичного мастера Scale Out.

## <a name="4-set-up-ssisdb-always-on"></a>4. Настройка AlwaysOn для SSISDB

Инструкции по настройке AlwaysOn для SSISDB приводятся в разделе [AlwaysOn для каталога служб SSIS (SSISDB)](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb).

Кроме того, необходимо создать прослушиватель группы доступности для группы доступности, в которую была добавлена SSISDB. См. раздел [Создание или настройка прослушивателя группы доступности](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).

## <a name="5-update-scale-out-master-service-configuration-file"></a>5. Обновление файла конфигурации для службы мастера Scale Out
Обновите файл конфигурации для службы мастера Scale Out (\<диск\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config) на основном и вторичном узлах. Присвойте атрибуту **SqlServerName** значение *[имя DNS прослушивателя группы доступности],[порт]*.

## <a name="6-enable-package-execution-logging"></a>6. Включение ведения журнала выполнения пакетов

Ведение журналов в SSISDB реализуется посредством входа в **##MS_SSISLogDBWorkerAgentLogin##**, пароль для которого формируется автоматически. Чтобы настроить ведение журналов для всех реплик SSISDB, выполните следующие действия.

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-primary-sql-server"></a>6.1. Смените пароль **##MS_SSISLogDBWorkerAgentLogin##** на основном экземпляре Sql Server.
### <a name="62-add-the-login-to-secondary-sql-server"></a>6.2. Добавьте имя входа для вторичного экземпляра Sql Server.
### <a name="63-update-connection-string-of-logging"></a>6.3. Обновите строку подключения для ведения журналов.
Вызовите хранимую процедуру [catalog].[update_logdb_info] с параметрами 

@server_name = '*[имя DNS прослушивателя группы доступности],[порт]*' 

и @connection_string = 'Data Source=*[имя DNS прослушивателя группы доступности]*,*[порт]*;Initial Catalog=SSISDB;User Id=##MS_SSISLogDBWorkerAgentLogin##;Password=*[пароль]*];'.

## <a name="7-congifure-scale-out-master-service-role-of-windows-failover-cluster"></a>7. Настройка роли службы мастера Scale Out для отказоустойчивого кластера Windows

В диспетчере отказоустойчивого кластера установите подключение между Scale Out и кластером. Выберите кластер и щелкните **Действие** в меню, после чего выберите **Настроить роль...**.

Во всплывающем окне **Мастер высокой доступности** выберите **Универсальная служба** на странице **Выбор роли** и затем выберите "Мастер SQL Server Integration Services Scale Out 14.0" на странице **Выбор службы**.

На странице **Точка доступа клиента** введите имя узла DNS службы мастера Scale Out.

![Мастер высокой доступности 1](media/ha-wizard1.PNG)

Завершите работу мастера.

## <a name="8-update-master-address-in-ssisdb"></a>8. Обновление адреса мастера в SSISDB

На основном сервере SQL выполните хранимую процедуру [SSIS].[catalog].[update_master_address] с параметром @MasterAddress = N'https://[имя узла DNS службы мастера Scale Out]:[порт мастера]'. 

## <a name="9-add-scale-out-worker"></a>9. Добавление рабочей роли Scale Out

Теперь можно добавить рабочие роли Scale Out с помощью [диспетчера Scale Out](integration-services-ssis-scale-out-manager.md). Введите *[имя DNS прослушивателя группы доступности SQL Server]*,*[порт]* на странице подключения.




