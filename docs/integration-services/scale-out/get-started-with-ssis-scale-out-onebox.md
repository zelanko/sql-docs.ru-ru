---
title: Начало работы с SSIS Scale Out на одном компьютере | Документы Майкрософт
description: В этой статье приводятся все сведения, необходимые для того, чтобы начать работу с SSIS Scale Out на одном компьютере.
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 09c9765791f68f1026e906f797ac0d00b915866f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811572"
---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Начало работы с SSIS Scale Out на одном компьютере
В этом разделе приводятся рекомендации по настройке компонента Integration Services Scale Out в среде с одним компьютером с параметрами по умолчанию.

## <a name="1-install-sql-server-features"></a>1. Установка компонентов SQL Server
В мастере SQL Server на странице **Выбор компонентов** выберите следующие элементы:
-   Службы ядра СУБД
-   Службы Integration Services
    -   Мастер Scale Out
    -   Рабочая роль Scale Out

![Первая половина списка на странице "Выбор компонентов"](media/feature-select-onebox1.PNG)

![Вторая половина списка на странице "Выбор компонентов"](media/feature-select-onebox2.PNG)

На странице **Конфигурация сервера** нажмите кнопку **Далее**, чтобы принять учетные записи служб и типы запуска по умолчанию.

На странице **Настройка ядра СУБД** установите переключатель в положение **Смешанный режим** и нажмите кнопку **Добавить текущего пользователя**. 

![Настройка ядра СУБД](media/engine-config.PNG)

На страницах **Настройка развертывания служб Integration Services — главный узел** и **Настройка развертывания служб Integration Services — рабочий узел** нажмите кнопку **Далее**, чтобы применить параметры по умолчанию для порта и сертификатов.

Завершите работу мастера установки SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Установка SQL Server Management Studio

Скачайте и установите [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="3-enable-scale-out"></a>3. Включение Scale Out
Откройте среду SQL Server Management Studio и подключитесь к локальному экземпляру SQL Server.
В обозревателе объектов щелкните правой кнопкой мыши узел **Каталоги служб Integration Services** и выберите пункт **Создать каталог**.

В диалоговом окне **Создать каталог** параметр **Включить этот сервер в качестве мастера масштабирования SSIS** выбран по умолчанию.

## <a name="4-enable-a-scale-out-worker"></a>4. Включение рабочей роли Scale Out
В SQL Server Management Studio (SSMS) щелкните правой кнопкой мыши элемент **SSISDB** и выберите пункт **Управление развертыванием**. 

![Управление Scale Out](media/manage-scale-out.PNG)

Откроется диспетчер Integration Services Scale Out. Дополнительные сведения см. в разделе [Диспетчер Scale Out](integration-services-ssis-scale-out-manager.md).

Чтобы включить рабочую роль Scale Out, перейдите в **диспетчер рабочих ролей** и выберите рабочую роль, которую нужно включить. Рабочие роли по умолчанию отключены. Чтобы включить выбранную рабочую роль, щелкните **Включить рабочую роль**.

## <a name="5-run-packages-in-scale-out"></a>5. Выполнение пакетов в масштабном развертывании
Теперь пакеты служб SSIS можно запускать в Scale Out. Дополнительные сведения см. в статье [Выполнение пакетов в масштабном развертывании служб Integration Services (SSIS)](run-packages-in-integration-services-ssis-scale-out.md).

## <a name="next-steps"></a>Следующие шаги
-   [Добавление рабочей роли Scale Out с помощью диспетчера Scale Out](add-scale-out-worker.md)
