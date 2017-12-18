---
title: "Начало работы с SSIS Scale Out на одном компьютере | Документы Майкрософт"
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
ms.openlocfilehash: 8514cd548b003a39bf198b83b6b80d775a55384b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Начало работы с SSIS Scale Out на одном компьютере
В этом разделе приводятся рекомендации по настройке компонента Integration Services Scale Out в среде с одним компьютером с параметрами по умолчанию.

## <a name="1-install-sql-server-features"></a>1. Установка компонентов SQL Server
В мастере установки SQL Server на странице **Выбор компонентов** выберите компоненты "Службы ядра СУБД", "Службы Integration Services", "Мастер масштабирования" и "Рабочая роль масштабирования".

![Страница "Выбор компонентов" — снимок экрана 1](media/feature-select-onebox1.PNG)

![Страница "Выбор компонентов" — снимок экрана 2](media/feature-select-onebox2.PNG)

На странице **Конфигурация сервера** просто нажмите кнопку "Далее", чтобы использовать учетные записи служб и типы запуска по умолчанию.

На странице **Настройка ядра СУБД** установите переключатель в положение **Смешанный режим** и нажмите кнопку **Добавить текущего пользователя**. 

![Настройка ядра СУБД](media/engine-config.PNG)

На страницах **Настройка развертывания служб Integration Services — главный узел** и **Настройка развертывания служб Integration Services — рабочий узел** просто нажмите кнопку "Далее", чтобы применить параметры по умолчанию для порта и сертификатов.

Завершите работу мастера установки SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Установка SQL Server Management Studio

[Скачайте](../../ssms/download-sql-server-management-studio-ssms.md) среду SQL Server Management Studio и установите ее.

## <a name="3-enable-scale-out"></a>3. Включение Scale Out
Откройте среду SQL Server Management Studio и подключитесь к локальному экземпляру SQL Server.
В обозревателе объектов щелкните правой кнопкой мыши узел **Каталоги служб Integration Services** и выберите пункт **Создать каталог**.

В диалоговом окне **Создать каталог** параметр **Включить этот сервер в качестве мастера масштабирования SSIS** выбран по умолчанию. Просто создайте каталог обычным образом. 

## <a name="4-enable-scale-out-worker"></a>4. Включение рабочей роли Scale Out
В SQL Server Management Studio (SSMS) щелкните правой кнопкой мыши элемент **SSISDB** и выберите пункт **Управление развертыванием...**. ![Управление Scale Out](media/manage-scale-out.PNG)

Появится диспетчер Integration Services Scale Out. С его помощью можно управлять компонентом Scale Out. Дополнительные сведения см. в разделе [Диспетчер Integration Services Scale Out](integration-services-ssis-scale-out-manager.md).

Чтобы включить рабочую роль Scale Out, перейдите в **диспетчер рабочих ролей** и выберите рабочую роль, которую нужно включить. Рабочая роль изначально отключена. Чтобы включить ее, щелкните **Включить рабочую роль**.

## <a name="5-run-packages-in-scale-out"></a>5. Выполнение пакетов в масштабном развертывании
Теперь пакеты служб SSIS можно запускать в Scale Out. См. раздел [Выполнение пакетов в масштабном развертывании служб Integration Services (SSIS)](run-packages-in-integration-services-ssis-scale-out.md).


Инструкции по добавлению дополнительных рабочих ролей Scale Out см. в разделе [Добавление рабочей роли масштабного развертывания с помощью диспетчера масштабного развертывания](add-scale-out-worker.md).
