---
title: "Диспетчер SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт"
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
ms.openlocfilehash: 84fe58d4dc7894728c43cb19d17d3444b5b84820
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-scale-out-manager"></a>Диспетчер Integration Services Scale Out

Диспетчер Scale Out обеспечивает централизованное управление всей топологией SSIS Scale Out. Его применение устраняет необходимость работы на нескольких компьютерах и использования команд TSQL. 

Запустить диспетчер Scale Out можно двумя способами.

## <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1. Запуск диспетчера Scale Out из SQL Server Management Studio
Откройте SQL Server Management Studio и подключитесь к экземпляру SQL Server мастера Scale Out.

Щелкните правой кнопкой мыши **SSISDB** в обозревателе объектов и выберите пункт **Управление Scale Out...** ![Управление Scale Out](media/manage-scale-out.PNG)

> [!NOTE]
> Рекомендуется запускать SQL Server Management Studio от имени администратора, поскольку для выполнения операций по управлению Scale Out, таких как "Добавление рабочей роли Scale Out", требуются права администратора.


## <a name="2-open-scale-out-manager-by-runing-ismanagerexe-directly"></a>2. Запуск диспетчера Scale Out с помощью ISManager.exe

Файл ISManager.exe находится в папке %системный_диск%\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn\Management. Щелкните правой кнопкой мыши файл **ISManager.exe** и выберите команду "Запуск от имени администратора". 

После открытия файла необходимо ввести имя SQL Server для мастера Scale Out и установить подключение к нему, после чего станут доступны функции управления Scale Out.

![Подключение на портале](media/portal-connect.PNG)

Диспетчер Scale Out реализует широкий спектр функций, показанных ниже. 

## <a name="enable-scale-out"></a>Включение Scale Out
Если режим Scale Out не включен, его можно активировать с помощью соответствующей кнопки после подключения к SQL Server.

![Включение Scale Out на портале](media/portal-enable-scale-out.PNG) 
## <a name="view-scale-out-master-status"></a>Просмотр состояния мастера Scale Out
Сведения о состоянии мастера Scale Out отображаются на странице **Панель мониторинга**.

![Панель мониторинга на портале](media/portal-dashboard.PNG)
## <a name="view-scale-out-worker-status"></a>Просмотр состояния рабочей роли Scale Out
Состояние рабочей роли Scale Out отображается на странице **Диспетчер рабочих ролей**. Чтобы просмотреть состояние отдельной рабочей роли, щелкните ее.

![Диспетчер рабочих ролей на портале](media/portal-worker-manager.PNG)

## <a name="add-scale-out-worker"></a>Добавление рабочей роли Scale Out
Чтобы добавить рабочую роль Scale Out, нажмите кнопку "+" внизу списка рабочих ролей Scale Out. 

Введите имя компьютера для рабочей роли Scale Out, которую требуется добавить, и щелкните "Проверить". Диспетчер Scale Out проверит наличие у текущего пользователя прав доступа к хранилищу сертификатов на компьютерах с мастером Scale Out и рабочей ролью Scale Out.

![Подключение рабочей роли](media/connect-worker.PNG)

В случае успешного прохождения проверки диспетчер Scale Out пытается считать файл конфигурации рабочей роли и получить отпечаток сертификата для нее. Дополнительные сведения см. в разделе [Рабочая роль Scale Out](integration-services-ssis-scale-out-worker.md). Если считать файл конфигурации рабочей роли не удается, предоставить сертификат рабочей роли можно двумя способами. 

Вы можете ввести отпечаток сертификата рабочей роли напрямую 

![Сертификат рабочей роли 1](media/portal-cert1.PNG)

или предоставить файл сертификата. 

![Сертификат рабочей роли 2](media/portal-cert2.PNG)

После сбора всех сведений диспетчер Scale Out предоставит действия, которые необходимо выполнить. Как правило, требуется установить сертификат, обновить файл конфигурации рабочей роли и перезапустить службу рабочей роли. 

![Подтверждение добавления на портале 1](media/portal-add-confirm1.PNG)

Если сертификат рабочей роли недоступен, необходимо обновить его вручную или перезапустить службу рабочей роли.

![Подтверждение добавления на портале 2](media/portal-add-confirm2.PNG)

Установите флажок подтверждения и начните добавление рабочей роли Scale Out.

## <a name="delete-scale-out-worker"></a>Удаление рабочей роли Scale Out
Чтобы удалить рабочую роль Scale Out, выберите ее и нажмите кнопку "-" внизу списка рабочих ролей Scale Out.


## <a name="enabledisable-scale-out"></a>Включение и отключение Scale Out
Чтобы включить или отключить рабочую роль Scale Out, выберите ее и затем нажмите кнопку "Включить рабочую роль" или "Отключить рабочую роль" соответственно. Если рабочая роль не находится в автономном режиме, ее состояние в диспетчере Scale Out изменится соответствующим образом.

## <a name="edit-scale-out-worker-description"></a>Изменение описания рабочей роли Scale Out
Чтобы изменить описание рабочей роли Scale Out, выберите ее и нажмите кнопку "Изменить". После внесения изменений нажмите кнопку "Сохранить".

![Сохранение рабочей роли на портале](media/portal-save-worker.PNG)

