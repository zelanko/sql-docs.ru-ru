---
title: Настройка оценки SQL для SQL Server с поддержкой Azure Arc
titleSuffix: ''
description: Настройка оценки по запросу для экземпляра SQL Server с поддержкой Azure Arc.
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: f3d2051e7003407a4ba7cbb3fb2ff8682ec6ee8f
ms.sourcegitcommit: 8f062015c2a033f5a0d805ee4adabbe15e7c8f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "91227327"
---
# <a name="configure-on-demand-sql-assessment-for-azure-arc-enabled-sql-server-instance"></a>Настройка оценки SQL по запросу для экземпляра SQL Server с поддержкой Azure Arc

Вы можете включить оценку SQL для экземпляров SQL Server, выполнив следующие действия.

## <a name="prerequisites"></a>Предварительные требования

* Ваш экземпляр SQL Server должен быть подключен к Azure Arc. Выполните инструкции по [подключению экземпляра SQL Server к SQL Server с поддержкой Arc](connect.md).

* На компьютере должно быть установлено и настроено расширение MMA. Выполните следующие инструкции: [Установка Microsoft Monitoring Agent (MMA)](configure-advanced-data-security.md#install-microsoft-monitoring-agent-mma). Дополнительные сведения: [Агент Log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/log-analytics-agent).

* Для SQL Server необходимо [включить протокол TCP/IP](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).

* При работе с именованным экземпляром SQL Server необходимо запустить [Обозреватель SQL Server](../../tools/configuration-manager/sql-server-browser-service.md).

* Вам нужно ознакомиться с документом по SQL Server в разделе [Предварительные требования для оценок по запросу Центра служб](https://docs.microsoft.com/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents).

## <a name="enable-on-demand-sql-assessment"></a>Включение оценки SQL по запросу

1. Откройте свой ресурс SQL Server — Azure Arc и выберите __Работоспособность среды__ в меню слева.

   ![Выбор оценки SQL](media/assess/sql-assessment-heading-sql-server-arc.png)

1. Укажите рабочую папку на компьютере для сбора данных. По умолчанию будет использоваться `C:\sql_assessment\work_dir`. Данные будут временно храниться в этой папке в ходе сбора и анализа. Если папка не существует, она будет создана автоматически.

1. Щелкните __Скачать сценарий конфигурации__ и скопируйте скачанный сценарий на целевой компьютер.

1. Запустите экземпляр администратора __powershell.exe__ и выполните одно из следующих действий. 
   * Если используется учетная запись домена, выполните следующие команды. Отобразится запрос об учетной записи и пароле. 

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1'
      ```

    * Если используется учетная запись MSA, выполните следующие команды.

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1' -ManagedServiceAccountName <MSA account name>
      ```

   > [!NOTE]
   > Сценарий запланирует задачу с именем *SQLAssessment*, которая будет запущена в течение часа после выполнения предыдущего сценария, а затем будет выполняться каждые 7 дней. Дату и время задачи можно изменить или запустить ее сразу, выбрав библиотеку планировщика заданий > "Майкрософт" > Operations Management Suite > AOI*** > "Оценки" > SQLAssessment. Эта задача активирует сбор данных.

## <a name="view-the-assessment-results"></a>Просмотр результатов оценки

Кнопка __Просмотр результатов оценки SQL__ в колонке _Работоспособность среды_ отключена, пока результаты в Log Analytics не будут готовы. Как только она станет доступна, щелкните ее для просмотра результатов. После обработки файлов данных на целевом компьютере отображение результатов в Log Analytics может занять до 2 часов.

![Результаты оценки SQL](media/assess/sql-assessment-results.png)

Узнать состояние обработки данных на компьютере для сбора можно, просмотрев файлы в рабочей папке. После завершения запланированной задачи вы увидите несколько файлов с префиксом _new._ в рабочей папке:

![Готовые файлы данных](media/assess/sql-assessment-data-files-ready.png)

Microsoft Monitoring Agent сканирует рабочую папку на наличие файлов _new.*_ раз в 15 минут и отправляет данные в рабочую область Log Analytics. После отправки файла префикс изменяется с _new._ на _processed._ :

![Обработанные файлы данных](media/assess/sql-assessment-data-files-processed.png)

## <a name="next-steps"></a>Дальнейшие действия

Для получения дополнительных сведений ознакомьтесь с документом по SQL Server в разделе [Предварительные требования для оценок по запросу Центра служб](https://docs.microsoft.com/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents).

Комплексная поддержка для Оценки SQL по запросу предоставляется при наличии подписки с Единой поддержкой или поддержкой Premier. Дополнительные сведения: [Поддержка Premier для Azure](https://azure.microsoft.com/support/plans/premier).
