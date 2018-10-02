---
title: Диспетчер SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
description: В этой статье описывается средство "Диспетчер Scale Out", с помощью которого можно управлять компонентом SSIS Scale Out.
ms.custom: performance
ms.date: 12/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 53235c3c95c6c943ac340aecfaa8a62ff347a753
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659762"
---
# <a name="integration-services-scale-out-manager"></a>Диспетчер Integration Services Scale Out

Диспетчер Scale Out — это средство, которое обеспечивает централизованное управление всей топологией SSIS Scale Out. Оно избавляет от необходимости выполнять задачи управления и команды Transact-SQL на нескольких компьютерах.

## <a name="open-scale-out-manager"></a>Открытие диспетчера Scale Out

Открыть диспетчер Scale Out можно двумя способами.

### <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1. Запуск диспетчера Scale Out из SQL Server Management Studio
Откройте SQL Server Management Studio (SSMS) и подключитесь к экземпляру SQL Server мастера Scale Out.

В обозревателе объектов щелкните правой кнопкой мыши узел **SSISDB** и выберите пункт **Управление развертыванием**.

![Управление Scale Out](media/manage-scale-out.PNG)

> [!NOTE]
> Рекомендуется запускать SQL Server Management Studio от имени администратора, так как для выполнения некоторых операций по управлению Scale Out, таких как добавление рабочей роли Scale Out, требуются права администратора.

### <a name="2-open-scale-out-manager-by-running-managementtoolexe"></a>2. Открытие диспетчера Scale Out с помощью программы ManagementTool.exe

Найдите файл `ManagementTool.exe` в папке `%SystemDrive%\Program Files (x86)\Microsoft SQL Server\150\DTS\Binn\Management`. Щелкните файл **ManagementTool.exe** правой кнопкой мыши и выберите пункт **Запуск от имени администратора**. 

Когда диспетчер Scale Out откроется, введите имя экземпляра SQL Server для мастера Scale Out и установите подключение к нему для управления средой Scale Out.

![Подключение на портале](media/portal-connect-new.png)

## <a name="tasks-available-in-scale-out-manager"></a>Задачи, доступные в диспетчере Scale Out
В диспетчере Scale Out вы можете выполнять указанные ниже действия.

### <a name="enable-scale-out"></a>Включение Scale Out
После подключения к SQL Server, если режим Scale Out не включен, его можно активировать, нажав кнопку **Включить**.

![Включение Scale Out на портале](media/portal-enable-scale-out-new.PNG) 

### <a name="view-scale-out-master-status"></a>Просмотр состояния мастера Scale Out
Сведения о состоянии мастера Scale Out отображаются на странице **Панель мониторинга**.

![Панель мониторинга на портале](media/portal-dashboard-new.PNG)

### <a name="view-scale-out-worker-status"></a>Просмотр состояния рабочей роли Scale Out
Состояние рабочей роли Scale Out отображается на странице **Диспетчер рабочих ролей**. Чтобы просмотреть состояние отдельной рабочей роли, выберите ее.

![Диспетчер рабочих ролей на портале](media/portal-worker-manager-new.PNG)

### <a name="add-a-scale-out-worker"></a>Добавление рабочей роли Scale Out
Чтобы добавить рабочую роль Scale Out, нажмите кнопку **+** внизу списка рабочих ролей Scale Out. 

Введите имя компьютера для рабочей роли Scale Out, которую требуется добавить, и нажмите кнопку **Проверить**. Диспетчер Scale Out проверит наличие у текущего пользователя прав доступа к хранилищам сертификатов на компьютерах с мастером Scale Out и рабочей ролью Scale Out.

![Подключение рабочей роли](media/connect-worker-new.PNG)

В случае успешного прохождения проверки диспетчер Scale Out пытается считать файл конфигурации для службы рабочей роли и получить отпечаток сертификата для нее. Дополнительные сведения см. в разделе [Рабочая роль Scale Out](integration-services-ssis-scale-out-worker.md). Если считать файл конфигурации для службы рабочей роли не удается, предоставить сертификат рабочей роли можно двумя способами. 

- Вы можете ввести отпечаток сертификата рабочей роли напрямую.

    ![Сертификат рабочей роли 1](media/portal-cert1-new.PNG)

- Вы также можете предоставить файл сертификата.

    ![Сертификат рабочей роли 2](media/portal-cert2-new.PNG)

После сбора сведений диспетчер Scale Out предоставит указания по выполнению необходимых действий. Как правило, эти действия включают установку сертификата, обновление файла конфигурации для службы рабочей роли и перезапуск этой службы.

![Подтверждение добавления на портале 1](media/portal-add-confirm1-new.PNG)

Если вариант рабочей роли недоступен, необходимо обновить его вручную и перезапустить службу рабочей роли.

![Подтверждение добавления на портале 2](media/portal-add-confirm2-new.PNG)

Установите флажок **Подтвердить** и нажмите кнопку **ОК**, чтобы приступить к добавлению рабочей роли Scale Out.

### <a name="delete-a-scale-out-worker"></a>Удаление рабочей роли Scale Out
Чтобы удалить рабочую роль Scale Out, выберите ее и нажмите кнопку **-** внизу списка рабочих ролей Scale Out.

### <a name="enable-or-disable-a-scale-out-worker"></a>Включение или отключение рабочей роли Scale Out
Чтобы включить или отключить рабочую роль Scale Out, выберите ее и нажмите кнопку **Включить рабочую роль** или **Отключить рабочую роль**. Если рабочая роль не находится в автономном режиме, ее состояние в диспетчере Scale Out изменится соответствующим образом.

## <a name="edit-a-scale-out-worker-description"></a>Изменение описания рабочей роли Scale Out
Чтобы изменить описание рабочей роли Scale Out, выберите ее и нажмите кнопку **Изменить**. Завершив изменение описания, нажмите кнопку **Сохранить**.

![Сохранение рабочей роли на портале](media/portal-save-worker-new.PNG)

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения см. в следующих статьях:
-   [Главная роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-master.md)
-   [Рабочая роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-worker.md)
