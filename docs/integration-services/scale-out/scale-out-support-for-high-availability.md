---
title: Поддержка высокого уровня доступности в SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
description: В этой статье описывается настройка высокой доступности для SSIS Scale Out.
ms.custom: performance
ms.date: 05/23/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.openlocfilehash: a7c0e9b1d3315edb314cc95980fec8e18d544d0d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064564"
---
# <a name="scale-out-support-for-high-availability"></a>Поддержка высокого уровня доступности в Scale Out

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



В SSIS Scale Out высокий уровень доступности на стороне рабочей роли Scale Out обеспечивается за счет выполнения пакетов с использованием нескольких рабочих ролей Scale Out.

Высокий уровень доступности на стороне мастера Scale Out достигается за счет применения функций [AlwaysOn для каталога служб SSIS](../catalog/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) и отказоустойчивого кластера Windows. В этом решении несколько экземпляров мастера Scale Out размещаются в отказоустойчивом кластере Windows. Если служба мастера Scale Out или SSISDB на основном узле отключены, служба или SSISDB на вторичном узле продолжают принимать запросы пользователей и взаимодействовать с рабочими ролями Scale Out.

Кроме того, высокий уровень доступности на стороне мастера Scale Out Master может быть достигнут с использованием экземпляра отказоустойчивого кластера SQL Server. См. раздел [Поддержка Scale Out для обеспечения высокой доступности с помощью экземпляра отказоустойчивого кластера SQL Server](scale-out-failover-cluster-instance.md).

Чтобы настроить высокий уровень доступности на стороне мастера Scale Out с использованием функций AlwaysOn для каталога служб SSIS, выполните указанные ниже действия:

## <a name="1-prerequisites"></a>1. предварительные требования
Настроить отказоустойчивый кластер Windows. Инструкции см. в записи блога [Установка компонента и средств отказоустойчивого кластера для Windows Server 2012](https://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx). Установите компоненты и средства на всех узлах кластера.

## <a name="2-install-scale-out-master-on-the-primary-node"></a>2. Установка мастера Scale Out в основном узле
Установите службы ядра СУБД SQL Server, службы Integration Services и мастер Scale Out в основном узле для мастера Scale Out. 

Во время установки выполните указанные ниже действия.

### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1. Настройте учетную запись, с помощью которой выполняется служба мастера Scale Out, в качестве учетной записи домена.
Эта учетная запись должна впоследствии иметь доступ к SSISDB во вторичном узле в отказоустойчивом кластере Windows. Так как служба мастера Scale Out и SSISDB реализуют отдельную отработку отказа, они не могут находиться на одном узле после отработки отказа.

![Конфигурация сервера высокой доступности](media/ha-server-config.PNG)

### <a name="22-include-the-dns-host-name-for-the-scale-out-master-service-in-the-cns-of-the-scale-out-master-certificate"></a>2.2. Включите имя узла DNS для службы мастера Scale Out в список CN для сертификата мастера Scale Out.

Это имя узла — конечная точка мастера Scale Out, которая создается как кластеризованная универсальная служба в отказоустойчивом кластере (см. шаг 7).   (Необходимо указать имя узла DNS, а не имя сервера.)

![Конфигурация мастера высокой доступности](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-the-secondary-node"></a>3. Установка мастера Scale Out во вторичном узле
Установите службы ядра СУБД SQL Server, службы Integration Services и мастер Scale Out во вторичном узле для мастера Scale Out. 

Используйте тот же сертификат мастера Scale Out, что и в основном узле. Экспортируйте SSL-сертификат мастера Scale Out в основном узле с закрытым ключом и установите его в корневое хранилище сертификатов локального компьютера во вторичном узле. Выберите этот сертификат при установке мастера Scale Out во вторичном узле.

![Конфигурация мастера высокой доступности 2](media/ha-master-config2.PNG)

> [!NOTE]
> Вы можете настроить несколько резервных мастеров Scale Out, повторив эти действия для мастера Scale Out в других вторичных узлах.

## <a name="4-set-up-and-configure-ssisdb-support-for-always-on"></a>4. Настройка поддержки SSISDB для AlwaysOn

Выполните инструкции по настройке поддержки SSISDB для AlwaysOn, приведенные в статье об [AlwaysOn для каталога служб SSIS (SSISDB)](../catalog/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb).

Кроме того, необходимо создать прослушиватель группы доступности для группы доступности, в которую добавляется SSISDB. См. раздел [Создание или настройка прослушивателя группы доступности](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).

## <a name="5-update-the-scale-out-master-service-configuration-file"></a>5. Обновление файла конфигурации для службы мастера Scale Out
Обновите файл конфигурации для службы мастера Scale Out (`\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config`) в основном и вторичном узлах. Присвойте атрибуту **SqlServerName** значение *[имя DNS прослушивателя группы доступности],[порт]* .

## <a name="6-enable-package-execution-logging"></a>6. Включение ведения журнала выполнения пакетов

Ведение журналов в SSISDB реализуется посредством имени входа **##MS_SSISLogDBWorkerAgentLogin##** , пароль для которого формируется автоматически. Чтобы настроить ведение журналов для всех реплик SSISDB, выполните указанные ниже действия.

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-the-primary-sql-server"></a>6.1. Смените пароль для **##MS_SSISLogDBWorkerAgentLogin##** в основном экземпляре SQL Server.

### <a name="62-add-the-login-to-the-secondary-sql-server"></a>6.2. Добавьте имя входа для вторичного экземпляра SQL Server.

### <a name="63-update-the-connection-string-used-for-logging"></a>6.3. Обновите строку подключения, используемую для ведения журналов.
Вызовите хранимую процедуру `[catalog].[update_logdb_info]` со следующими значениями параметров:

-   `@server_name = '[Availability Group Listener DNS name],[Port]'`

-   `@connection_string = 'Data Source=[Availability Group Listener DNS name],[Port];Initial Catalog=SSISDB;User Id=##MS_SSISLogDBWorkerAgentLogin##;Password=[Password]];'`

## <a name="7-configure-the-scale-out-master-service-role-of-the-windows-server-failover-cluster"></a>7. Настройка роли службы мастера Scale Out для отказоустойчивого кластера Windows Server

1.  В диспетчере отказоустойчивости кластеров установите подключение к кластеру для Scale Out. Выберите кластер. Выберите в меню пункт **Действие**, после чего выберите **Настроить роль**.

2.  В диалоговом окне **Мастер высокой доступности** выберите **Универсальная служба** на странице **Выбор роли**. На странице **Выбор службы** выберите "Главная служба развертывания SQL Server Integration Services 14.0".

3.  На странице **Точка доступа клиента** введите имя узла DNS службы мастера Scale Out.

    ![Мастер высокой доступности 1](media/ha-wizard1.PNG)

4.  Завершите работу мастера.

Для этого шага на виртуальных машинах Azure нужны дополнительные действия. Полное описание этих основных понятий и шагов выходит за рамки данной статьи.

1.  Необходимо настроить домен Azure. Для работы отказоустойчивой кластеризации Windows Server нужно, чтобы все компьютеры в кластере входили в состав одного домена. Дополнительные сведения см. в статье [Включение доменных служб Azure Active Directory с помощью портала Azure](https://docs.microsoft.com/en-us/azure/active-directory-domain-services/create-instance).

2. Необходимо настроить балансировщик нагрузки Azure. Это требование для прослушивателя группы доступности. Дополнительные сведения см. в статье [Руководство по балансировке нагрузки внутреннего трафика на виртуальных машинах с помощью балансировщика нагрузки уровня "Базовый" на портале Azure](https://docs.microsoft.com/azure/load-balancer/tutorial-load-balancer-basic-internal-portal).

## <a name="8-update-the-scale-out-master-address-in-ssisdb"></a>8. Обновление адреса мастера Scale Out в SSISDB

На основном сервере SQL Server выполните хранимую процедуру `[catalog].[update_master_address]` со значением параметра `@MasterAddress = N'https://[Scale Out Master service DNS host name]:[Master Port]'`. 

## <a name="9-add-the-scale-out-workers"></a>9. Добавление рабочих ролей Scale Out

Теперь можно добавить рабочие роли Scale Out с помощью [диспетчера Integration Services Scale Out](integration-services-ssis-scale-out-manager.md). Введите `[SQL Server Availability Group Listener DNS name],[Port]` на странице подключения.

## <a name="upgrade-scale-out-in-high-availability-environment"></a>Обновление Scale Out в среде высокого уровня доступности
Чтобы обновить Scale Out в среде высокого уровня доступности, выполните [инструкции по обновлению из AlwaysOn для каталога служб SSIS](../catalog/ssis-catalog.md#Upgrade), обновите Scale Out и рабочие роли Scale Out на каждом компьютере, а также повторно создайте роль отказоустойчивого кластера Windows Server в шаге 7 выше с помощью новой версии службы мастера Scale Out.

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения см. в следующих статьях:
-   [Главная роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-master.md)
-   [Рабочая роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-worker.md)
