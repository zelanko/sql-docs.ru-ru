---
title: Пошаговое руководство. Настройка SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
description: В этой статье приводятся пошаговые инструкции по установке и настройке SSIS Scale Out.
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 1a3d2c0725035e4a985d44a8e06c69b47b3e2009
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35401186"
---
# <a name="walkthrough-set-up-integration-services-ssis-scale-out"></a>Пошаговое руководство. Настройка Integration Services (SSIS) Scale Out
Чтобы настроить [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] (SSIS) Scale Out, выполните указанные ниже задачи. 

> [!TIP]
> При установке Scale Out на одном компьютере следует устанавливать мастер Scale Out и рабочую роль Scale Out одновременно. При одновременной установке компонентов автоматически создается конечная точка для подключения к главной роли масштабного развертывания. 

* [Установка главной роли масштабного развертывания](#InstallMaster)

* [Установка рабочей роли масштабного развертывания](#InstallWorker)

* [Установка сертификата клиента рабочей роли масштабного развертывания](#InstallCert)

* [Открытие порта брандмауэра](#Firewall)

* [Запуск службы главной и рабочей роли масштабного развертывания](#Start)

* [Включение главной роли масштабного развертывания](#EnableMaster)

* [Включение режима проверки подлинности SQL Server](#EnableAuth)

* [Включение рабочей роли масштабного развертывания](#EnableWorker)

## <a name="InstallMaster"></a> Установка главной роли масштабного развертывания

Чтобы настроить мастер Scale Out, необходимо установить службы ядра СУБД, [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] и компонент мастера Scale Out при настройке [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. 

Сведения о настройке ядра СУБД и [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] см. в разделах [Установка ядра СУБД SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md) и [Установка служб Integration Services](../install-windows/install-integration-services.md).

> [!NOTE]
> Чтобы использовать учетную запись для проверки подлинности SQL Server по умолчанию для ведения журналов Scale Out, выберите смешанный режим проверки подлинности на странице **Настройка ядра СУБД** во время установки ядра СУБД. Дополнительные сведения см. в разделе [Изменение учетной записи для ведения журнала Scale Out](change-logdb-account.md).

Чтобы установить компонент мастера Scale Out, используйте мастер установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] или командную строку.

### <a name="install-scale-out-master-with-the-sql-server-installation-wizard"></a>Установка мастера Scale Out с помощью мастера установки SQL Server
1.  На странице **Выбор компонентов** выберите элемент **Мастер Scale Out** в категории [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  
    ![Выбор главной роли](media/feature-select-master.PNG)
  
2.  На странице **Конфигурация сервера** выберите учетную запись для запуска **службы главной роли масштабного развертывания SQL Server Integration Services** и **Тип запуска**.  
    ![Конфигурация сервера](media/server-config.PNG)

3.  На странице **Настройка мастера масштабирования служб Integration Services** укажите номер порта, который главная роль масштабного развертывания использует для связи с рабочей ролью. По умолчанию номер порта равен 8391.  

    ![Конфигурация мастера](media/master-config.PNG "Конфигурация мастера")

4.  Укажите SSL-сертификат, используемый для защиты связи между мастером и рабочей ролью Scale Out, выполнив одно из указанных ниже действий.
    * Позвольте процессу установки создать самозаверяющий SSL-сертификат по умолчанию, выбрав **Создать SSL-сертификат**.  Сертификат по умолчанию устанавливается в доверенных корневых центрах сертификации на локальном компьютере. Можно указать CN в этом сертификате. В список CN необходимо включить имя узла для конечной точки мастера. По умолчанию включаются имя компьютера и IP-адрес узла мастера.
    * Выберите существующий SSL-сертификат на локальном компьютере, щелкнув **Использовать существующий SSL-сертификат** и нажав кнопку **Обзор**. Отпечаток сертификата отображается в текстовом поле. При нажатии кнопки **Обзор** отображаются сертификаты, хранящиеся в доверенных корневых центрах сертификации на локальном компьютере. Выбранный вами сертификат должен храниться здесь.       

    ![Конфигурация мастера 2](media/master-config-2.PNG "Конфигурация мастера 2")
  
5.  Завершите работу мастера установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

### <a name="install-scale-out-master-from-the-command-prompt"></a>Установка мастера Scale Out из командной строки

Следуйте инструкциям в разделе [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Задайте параметры для мастера Scale Out, выполнив указанные ниже действия.
 
1.  Добавьте `IS_Master` в параметр `/FEATURES`.

2.  Настройте мастер Scale Out, указав следующие параметры и их значения:
    -   `/ISMASTERSVCACCOUNT`
    -   `/ISMASTERSVCPASSWORD`
    -   `/ISMASTERSVCSTARTUPTYPE`
    -   `/ISMASTERSVCPORT`
    -   Среда `/ISMasterSVCSSLCertCN` (необязательно)
    -   Среда `/ISMASTERSVCTHUMBPRINT` (необязательно)

    > [!NOTE]
    > Если мастер Scale Out не устанавливается вместе с ядром СУБД и экземпляр ядра СУБД является именованным, после установки необходимо настроить `SqlServerName` в файле конфигурации службы мастера Scale Out. Дополнительные сведения см. в разделе [Мастер Scale Out](integration-services-ssis-scale-out-master.md).

## <a name="InstallWorker"></a> Установка рабочей роли масштабного развертывания
 
Чтобы настроить рабочую роль Scale Out, следует установить [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] и компонент рабочей роли Scale Out в программе установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

Чтобы установить рабочую роль Scale Out, используйте мастер установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] или командную строку.

### <a name="install-scale-out-worker-with-the-sql-server-installation-wizard"></a>Установка рабочей роли Scale Out с помощью мастера установки SQL Server

1.  На странице **Выбор компонентов** выберите элемент **Рабочая роль Scale Out** в категории [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].

    ![Выбор рабочей роли](media/feature-select-worker.PNG)

2.  На странице **Конфигурация сервера** выберите учетную запись для запуска **службы рабочей роли масштабного развертывания SQL Server Integration Services** и выберите **Тип запуска**.

    ![Конфигурация сервера 2](media/server-config-2.PNG "Конфигурация сервера 2")

3.  На странице **Настройка рабочей роли масштабирования служб Integration Services** укажите конечную точку для связи с главной ролью масштабного развертывания. 

    - Для среды **с одним компьютером** конечная точка создается автоматически при одновременной установке мастера и рабочей роли Scale Out. 

    - Для среды с **несколькими компьютерами** конечная точка состоит из имени или IP-адреса компьютера с мастером Scale Out, а также номера порта, указанного во время установки мастера Scale Out.
   
    ![Конфигурация рабочей роли 1](media/worker-config.PNG " 1")    

    > [!NOTE]
    > Вы также можете пропустить настройку рабочей роли на этом этапе и связать рабочую роль Scale Out с мастером Scale Out после установки, используя [диспетчер Scale Out](integration-services-ssis-scale-out-manager.md).

4. Для среды с **несколькими компьютерами** укажите SSL-сертификат клиента, используемый для проверки мастера Scale Out. Для среды с **одним компьютером** указывать SSL-сертификат клиента не требуется. 
  
    Нажмите кнопку **Обзор** , чтобы найти файл сертификата (CER). Чтобы использовать SSL-сертификат по умолчанию, выберите файл `SSISScaleOutMaster.cer`, находящийся в папке `\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn` на компьютере, на котором установлен мастер Scale Out.   

    ![Конфигурация рабочей роли 2](media/worker-config-2.PNG "Конфигурация рабочей роли 2")

    > [!NOTE]
    > Если SSL-сертификат, используемый мастером Scale Out, является самозаверяющим, соответствующий SSL-сертификат клиента требуется установить на компьютере с рабочей ролью Scale Out. Если указать путь к файлу SSL-сертификата клиента на странице **Настройка рабочей роли масштабирования служб Integration Services**, он будет установлен автоматически; в противном случае требуется установить этот сертификат вручную позже. 
     
5. Завершите работу мастера установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

### <a name="install-scale-out-worker-from-the-command-prompt"></a>Установка рабочей роли Scale Out из командной строки

Следуйте инструкциям в разделе [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Задайте параметры для рабочей роли Scale Out, выполнив указанные ниже действия.

1.  Добавьте IS_Worker в параметр `/FEATURES`.

2. Настройте рабочую роль Scale Out, указав следующие параметры и их значения:
    -   `/ISWORKERSVCACCOUNT`
    -   `/ISWORKERSVCPASSWORD`
    -   `/ISWORKERSVCSTARTUPTYPE`
    -   Среда `/ISWORKERSVCMASTER` (необязательно)
    -   Среда `/ISWORKERSVCCERT` (необязательно)
 
## <a name="InstallCert"></a> Установка сертификата клиента рабочей роли масштабного развертывания

Во время установки рабочей роли Scale Out сертификат рабочей роли создается и устанавливается на компьютере автоматически. Кроме того, соответствующий сертификат клиента SSISScaleOutWorker.cer устанавливается в папку `\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn`. Чтобы мастер Scale Out проверял подлинность рабочей роли, следует добавить этот сертификат клиента в корневое хранилище локального компьютера, где находится мастер Scale Out.
  
Чтобы добавить сертификат клиента в корневое хранилище, дважды щелкните файл CER и нажмите кнопку **Установить сертификат** в диалоговом окне сертификата. Откроется **мастер импорта сертификатов**.  

## <a name="Firewall"></a> Открытие порта брандмауэра

На компьютере с мастером Scale Out откройте порт, указанный во время установки мастера Scale Out, и порт SQL Server (по умолчанию 1433) в брандмауэре Windows.

> [!Note]
> После открытия порта в брандмауэре требуется перезапустить службу рабочей роли Scale Out.
    
## <a name="Start"></a> Запуск службы главной и рабочей роли масштабного развертывания

Если во время установки для служб не был задан тип запуска **Автоматически**, запустите следующие службы:

-   Главная служба развертывания SQL Server Integration Services 14.0 (SSISScaleOutMaster140S)

-   Рабочая роль развертывания SQL Server Integration Services 14.0 (SSISScaleOutWorker140)

## <a name="EnableMaster"></a> Включение главной роли масштабного развертывания

При создании каталога SSISDB в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../../includes/ssmanstudio-md.md)] выберите параметр **Включить этот сервер в качестве мастера масштабирования SSIS** в диалоговом окне **Создать каталог**.

После создания каталога вы можете включить мастер Scale Out с помощью [диспетчера Scale Out](integration-services-ssis-scale-out-manager.md).

## <a name="EnableAuth"></a> Включение режима проверки подлинности SQL Server
Если проверка подлинности [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] не была включена во время установки ядра СУБД, включите режим проверки подлинности SQL Server в экземпляре [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], в котором находится каталог SSISDB. 

При отключенной проверке подлинности SQL Server выполнение пакетов не блокируется. Однако журнал выполнения не может записываться в базу данных SSISDB.

## <a name="EnableWorker"></a> Включение рабочей роли масштабного развертывания

Рабочую роль Scale Out можно включить с помощью [диспетчера Scale Out](integration-services-ssis-scale-out-manager.md), предоставляющего графический пользовательский интерфейс, или с помощью хранимой процедуры.

Чтобы включить рабочую роль Scale Out, выполните хранимую процедуру `[catalog].[enable_worker_agent]`, используя **WorkerAgentId** в качестве параметра. 

После регистрации рабочей роли Scale Out в мастере Scale Out вы получаете значение **WorkerAgentId** из представления `[catalog].[worker_agents]` в SSISDB. Регистрация занимает несколько минут после запуска служб мастера и рабочей роли Scale Out.

#### <a name="example"></a>Пример
В приведенном ниже примере рабочая роль Scale Out включается на компьютере `computerA`.

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName  --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    computerA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="next-steps"></a>Следующие шаги
-   [Выполнение пакетов в SQL Server Integration Services (SSIS) Scale Out](run-packages-in-integration-services-ssis-scale-out.md)
