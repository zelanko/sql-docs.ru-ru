---
title: "Начало работы с масштабом SSIS помещает на одном компьютере | Документы Microsoft"
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
ms.openlocfilehash: 7175c63be4c0e15e50f2020f75d283ac0e3dfdbf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="get-started-with-integration-services-ssis-scale-out-on-a-single-computer"></a>Начало работы с Integration Services (SSIS) масштабное развертывание на одном компьютере
Этот раздел содержит рекомендации настройки масштабирования службы интеграции, в среде одно поле с параметрами по умолчанию.

## <a name="1-install-sql-server-features"></a>1. Установка компонентов SQL Server
В мастере установки SQL Server, выберите службы компонента Database Engine, службы Integration Services, масштаб Out главного и масштаб Out работника на **Выбор компонентов** страницы.

![Выберите Onebox компонентов 1](media/feature-select-onebox1.PNG)

![Функция Select Onebox 2](media/feature-select-onebox2.PNG)

На **конфигурации сервера** просто нажмите кнопку «Далее», чтобы использовать учетные записи служб по умолчанию и типы запуска.

На **Настройка компонента Database Engine** выберите «**смешанного режима**«и нажмите кнопку»**добавить текущего пользователя**» кнопки. 

![Конфигурация ядра](media/engine-config.PNG)

Один **конфигурации Integration Services шкалы Out - главного узла** и **конфигурации Integration Services шкалы Out - рабочий узел** страниц, просто нажмите кнопку «Далее» для применения настроек по умолчанию, порт и сертификатов.

Завершите мастер установки SQL Server.

## <a name="2-install-sql-server-management-studio"></a>2. Установка SQL Server Management Studio

[Загрузить](../../ssms/download-sql-server-management-studio-ssms.md) SQL Server Management Studio и установите его.

## <a name="3-enable-scale-out"></a>3. Включение масштабирования
Откройте SSMS и подключитесь к локальному экземпляру Sql Server.
Щелкните правой кнопкой мыши **каталоги служб Integration Services** в обозревателе объектов и выбрать **создать каталог**.

В **создать каталог** диалоговом **включите этот сервер как масштабирование служб SSIS master** выбран по умолчанию. Просто создайте каталог обычным образом. 

## <a name="4-enable-scale-out-worker"></a>4. Включение масштабирования работника
В среде SSMS щелкните правой кнопкой мыши **SSISDB** и выберите **управление масштабное развертывание...** . 
![Управление горизонтального масштабирования](media/manage-scale-out.PNG)

Появится всплывающее окно интеграции шкалы ожидания диспетчера служб. Вы можете управлять масштабное развертывание с ним. Дополнительные сведения см. в разделе [интеграции шкалы ожидания диспетчера служб](integration-services-ssis-scale-out-manager.md).

Чтобы включить работника Out шкалы, перейдите в **диспетчера рабочих процессов** и выберите работника, вы хотите включить. Исполнитель изначально отключены. Нажмите кнопку **включить рабочий** для его включения.

## <a name="5-run-packages-in-scale-out"></a>5. Выполнение пакетов в масштабном развертывании
Теперь все готово для запуска пакетов служб SSIS в масштабное развертывание. В разделе [масштабировать выполнения пакетов служб Integration Services (SSIS)](run-packages-in-integration-services-ssis-scale-out.md).


Чтобы добавить дополнительные рабочие процессы масштабное развертывание, см. [добавить шкалы ожидания рабочий процесс с шкалы ожидания диспетчера](add-scale-out-worker.md).
