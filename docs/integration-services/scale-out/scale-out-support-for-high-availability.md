---
title: "SQL Server Integration Services (SSIS) масштабирования поддержка высокого уровня доступности | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2405235bcfa09d2cc49e007f4eae6975d9ebf7a5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="scale-out-support-for-high-availability"></a>Масштабное развертывание поддержка высокого уровня доступности

В SSIS масштабное развертывание стороне работника высокий уровень доступности обеспечивается выполнение пакетов с помощью нескольких Out работников для масштабирования.
Высокая доступность стороне главного достигается с [Always On для каталога служб SSIS](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) и отказоустойчивого кластера Windows. Несколько экземпляров шкалы Out Master размещаются в отказоустойчивом кластере Windows. Если служба шкалы Out Master или SSISDB не работает на основном узле, службы или SSISDB на вторичном узле будет продолжать принимать запросы пользователей и взаимодействовать с ними шкалы ожидания рабочих процессов. 

Настройка на стороне главного высокий уровень доступности, выполните следующие действия.

## <a name="1-prerequisites"></a>1. Предварительные требования
Настроить отказоустойчивый кластер Windows. Инструкции см. в записи блога [Установка компонентов и средств отказоустойчивого кластера для Windows Server 2012)](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Installing the Failover Cluster Feature and Tools for Windows Server 2012). Компоненты и средства необходимо установить на всех узлах кластера.

## <a name="2-install-scale-out-master-on-primary-node"></a>2. Установить масштаб Out главного на основном узле
Установка службы компонента Database Engine, службы Integration Services и масштаб Out главного на основном узле для масштабирования Out Master. 

Во время установки следует 
### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1 задайте учетной записи шкалы Out Master службы с учетной записью домена.
Эта учетная запись должна иметь доступ к SSISDB на вторичном узле в отказоустойчивом кластере Windows в будущем. Как служба шкалы Out главного и SSISDB можно отдельно отработки отказа, они не могут быть на том же узле.

![Конфигурация сервера высокой ДОСТУПНОСТИ](media/ha-server-config.PNG)

### <a name="22-include-scale-out-master-service-dns-host-name-in-the-cns-of-scale-out-master-certificate"></a>2,2 включают шкалы Out Master службы имя узла DNS в общих имен для масштабирования Out главного сертификата.

Имя этого узла будет использоваться в конечной точке шкалы Out Master. 

![Основной конфигурации высокого уровня ДОСТУПНОСТИ](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-secondary-node"></a>3. Установить масштаб Out Master на вторичном узле
Установка службы компонента Database Engine, службы Integration Services и масштаб Out главного на вторичном узле для масштабирования Out Master. 

Следует использовать один и тот же сертификат шкалы Out главного с основного узла. Экспортировать шкалы Out Master SSL-сертификат на основном узле с помощью закрытого ключа и установить его в корневое хранилище сертификатов loacl машины на вторичном узле. Выберите этот сертификат при установке шкалы Out Master.

![Основной конфигурации HA 2](media/ha-master-config2.PNG)

> [!Note]
> Можно настроить несколько резервного копирования шкалы Out образцов, повторив операций для дополнительного масштабирования ожидания базы данных Master.

## <a name="4-set-up-ssisdb-always-on"></a>4. Настройка SSISDB всегда на

Инструкции по настройке всегда на для SSISDB можно увидеть в [Always On для каталога служб SSIS (SSISDB)](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb).

Кроме того необходимо создать прослушиватель gourp доступности для группы доступности, добавления SSISDB. В разделе [Создание или настройка прослушивателя группы доступности](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).

## <a name="5-update-scale-out-master-service-configuration-file"></a>5. Обновить файл конфигурации службы шкалы Out Master
Файл конфигурации службы шкалы Out Master обновление \<драйвер\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config на первичных и вторичных узлах. Обновление **SqlServerName** для *[имя DNS прослушивателя группы доступности], [порт]*.

## <a name="6-enable-package-execution-logging"></a>6. Включение ведения журнала выполнения пакета

Ведения журналов в SSISDB выполняется путем входа **MS_SSISLogDBWorkerAgentLogin ##**, пароль которого является формируется автоматически. Чтобы сделать работает ведение журнала для всех реплик SSISDB, выполните следующие действия.

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-primary-sql-server"></a>6.1 изменение пароля **MS_SSISLogDBWorkerAgentLogin ##** на сервере-источнике Sql.
### <a name="62-add-the-login-to-secondary-sql-server"></a>6.2. Добавьте имя входа для сервера-получателя Sql.
### <a name="63-update-connection-string-of-logging"></a>6.3 Обновите строку соединения для ведения журнала.
Вызовите хранимую процедуру [catalog]. [update_logdb_info] с 

@server_name= "*[Имя DNS прослушивателя группы доступности], [порт]*" 

и @connection_string = "источник данных =*[имя DNS прослушивателя группы доступности]*,*[порт]*; Initial Catalog = SSISDB; ИД пользователя = MS_SSISLogDBWorkerAgentLogin ##; Пароль =*[пароль]*]; ".

## <a name="7-congifure-scale-out-master-service-role-of-windows-failover-cluster"></a>7. Роль службы Congifure шкалы Out Master отказоустойчивого кластера Windows

Диспетчер кластеров отработки отказа, подключитесь к кластеру для масштабное развертывание. Выберите кластер и нажмите кнопку **действие** в меню, а затем **настроить роль...** .

В стека вверх **мастер высокой доступности**выберите **Универсальная служба** в **выберите роль** странице и выберите SQL Server Integration служб шкалы Out Master 14.0 в **Выбор службы** страницы.

В **точки доступа клиента** введите имя узла DNS службы шкалы Out Master.

![HA мастер 1](media/ha-wizard1.PNG)

Завершите работу мастера.

## <a name="8-update-master-address-in-ssisdb"></a>8. Мастер обновления адрес в SSISDB

На основном сервере SQL выполните хранимую процедуру [службы SSIS]. [catalog]. [update_master_address] с параметром @MasterAddress = N'https: / / [имя узла службы шкалы Out главного DNS]: [порт Master] ". 

## <a name="9-add-scale-out-worker"></a>9. Добавить работника для горизонтального масштабирования

Теперь вы можете добавлять шкалы Out работников с помощью [шкалы ожидания диспетчера](integration-services-ssis-scale-out-manager.md). Введите *[SQL Server доступности группы DNS-имя прослушивателя]*,*[порт]* на странице подключения.





