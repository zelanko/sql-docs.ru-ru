---
title: Настройка оценки SQL по запросу для экземпляра SQL Server с поддержкой Azure Arc
description: Настройка оценки SQL по запросу для экземпляра SQL Server с поддержкой Azure Arc
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 459a49a4f2ed41b8e9d95c805431ff2c29a770fa
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257994"
---
# <a name="configure-sql-assessment-on-an-azure-arc-enabled-sql-server-instance"></a>Настройка оценки SQL для экземпляра SQL Server с поддержкой Azure Arc

Оценка SQL предоставляет механизм для вычисления конфигурации SQL Server. В этой статье приводятся инструкции по использованию оценки SQL в экземпляре SQL Server с поддержкой Azure Arc.

## <a name="prerequisites"></a>Предварительные требования

* Ваш экземпляр SQL Server должен быть подключен к службе Azure Arc. Инструкции см. в статье [Подключение SQL Server к Azure Arc](connect.md).

* На компьютере должно быть установлено и настроено расширение Microsoft Monitoring Agent (MMA). Инструкции см. в статье [Установка MMA](configure-advanced-data-security.md#install-microsoft-monitoring-agent-mma). Кроме того, дополнительные сведения см. в статье [Log Analytics Agent](/azure/azure-monitor/platform/log-analytics-agent).

* В экземпляре SQL Server должен быть [включен протокол TCP/IP](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).

* При работе с именованным экземпляром SQL Server должна быть запущена [служба обозревателя SQL Server](../../tools/configuration-manager/sql-server-browser-service.md).

* Убедитесь, что вы проверили документ по SQL Server в разделе [Предварительные требования для оценок по запросу Центра служб](/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents).

## <a name="run-on-demand-sql-assessment"></a>Выполнение оценки SQL по требованию

1. Откройте SQL Server — ресурс Azure Arc и выберите **Работоспособность среды** на панели слева.

   > [!div class="mx-imgBorder"]
   > [ ![Снимок экрана: экран "Работоспособность среды" в SQL Server. Ресурса Azure Arc.](media/assess/sql-assessment-heading-sql-server-arc.png) ](media/assess/sql-assessment-heading-sql-server-arc.png#lightbox)

1. Укажите рабочую папку на компьютере для сбора данных. По умолчанию используется `C:\sql_assessment\work_dir`. Во время сбора и анализа данные временно хранятся в этой папке. Если папка не существует, она будет создана автоматически.

1. Выберите **Загрузить скрипт конфигурации** . Скопируйте загруженный скрипт на целевой компьютер.

1. Откройте экземпляр **PowerShell.exe** с правами администратора и выполните один из следующих блоков кода:

   * _Учетная запись домена_ :  Вам будет предложено ввести учетную запись пользователя и пароль.

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1'
      ```

   * _Управляемая учетная запись службы (MSA)_

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1' -ManagedServiceAccountName <MSA account name>
      ```

> [!NOTE]
> Скрипт планирует задачу с именем *SQLAssessment* , которая запускает сбор данных. Эта задача выполняется в течение часа после выполнения скрипта. Затем она повторяется каждые семь дней.

> [!TIP]
> Вы можете изменить задачу, чтобы она выполнялась в другой день и время, или даже принудительно запустить ее немедленно. В библиотеке планировщика заданий найдите **Microsoft** > **Operations Management Suite** > **AOI\*\*\***  > **Assessments** > **SQLAssessment** .

## <a name="view-sql-assessment-results"></a>Просмотр результатов оценки SQL

* На панели _Работоспособность среды_ выберите **Представление результатов оценки SQL** .

   > [!NOTE]
   > Кнопка **Представление результатов оценки SQL** остается неактивной до тех пор, пока результаты не будут готовы в журнале аналитики. Этот процесс может занять до двух часов после обработки файлов данных на целевом компьютере.

   > [!div class="mx-imgBorder"]
   > [ ![Снимок экрана: результаты оценки SQL.](media/assess/sql-assessment-results.png) ](media/assess/sql-assessment-results.png#lightbox)

* Узнать состояние обработки данных на компьютере для сбора можно, просмотрев файлы в рабочей папке. После завершения запланированной задачи вы увидите несколько файлов с префиксом _new._ Префикс в рабочей папке.

   > [!div class="mx-imgBorder"]
   > [ ![Снимок экрана: окно диспетчера файлов, в котором отображаются новые файлы данных в рабочей папке.](media/assess/sql-assessment-data-files-ready.png) ](media/assess/sql-assessment-data-files-ready.png#lightbox)

* Microsoft Monitoring Agent сканирует рабочую папку каждые 15 минут. Он ищет _new.*_ и отправляет данные в рабочую область Log Analytics. После того как MMA отправит файл, префикс меняется с _new._ на _processed._

   > [!div class="mx-imgBorder"]
   > ![Снимок экрана: окно диспетчера файлов, отображающее обработанные файлы данных.](media/assess/sql-assessment-data-files-processed.png)

## <a name="next-steps"></a>Дальнейшие действия

* Дополнительные сведения можно получить, просмотрев предварительные документы в разделе [Предварительные требования для оценок по запросу Центра служб](/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents).

* Для получения комплексной поддержки функции оценки SQL по запросу требуется подписка уровня Premier или Unified. Дополнительные сведения см. в статье [Поддержка Azure Premier](https://azure.microsoft.com/support/plans/premier).
