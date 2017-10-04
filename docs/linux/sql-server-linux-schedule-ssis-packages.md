---
title: "Расписание выполнения пакетов служб SSIS в Linux с cron | Документы Microsoft"
description: "В этой статье показано, как расписание выполнения пакетов служб интеграции SQL Server в Linux с помощью службы cron."
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.date: 09/26/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 31d5fb63a9c2a4d8825aa39c6fa7e3377ddc8d91
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>Выполнение в Linux с cron пакетов служб интеграции SQL Server расписание

При работе с SQL Server Integration Services (SSIS) и SQL Server в Windows, можно автоматизировать выполнение пакетов служб SSIS с помощью агента SQL Server. При работе с SQL Server и служб SSIS в Linux, служебную программу агента SQL Server недоступен, расписание заданий в Linux. Вместо этого используйте **Cron** услуг, которые широко используются для платформ Linux для автоматизации выполнения пакета.

Эта статья содержит примеры, которые показывают, как автоматизировать выполнение пакетов служб SSIS. Примеры были написаны для выполнения в Red Hat Enterprise. Код похоже на других дистрибутивах Linux, например Ubuntu.

## <a name="prerequisites"></a>Предварительные требования

Перед использованием службы Cron для выполнения заданий, необходимо проверить, работает ли на компьютере службы Cron.

Используйте следующую команду, чтобы проверить состояние службы Cron.

`systemctl status crond.service`

Если служба не активна (то есть, не выполняется), обратитесь к администратору, чтобы установить и настроить службы Cron должным образом.

## <a name="create-jobs"></a>Создание заданий

Задание Cron — задачи, которые можно настроить регулярное выполнение с заданным интервалом. Задание может быть простым как команду, которая обычно бы ввести непосредственно в консоль или запуска от имени сценария оболочки.

Для упрощения управления и выполнения задач технического обслуживания рекомендуется помещать команды выполнения пакета в сценарий с описательным именем.

Ниже приведен простой пример сценарий, который содержит только одну команду для выполнения пакета. При необходимости можно добавить дополнительные команды.

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Планирование заданий в службе Cron

После определения заданий, можно запланировать их автоматический запуск с помощью службы Cron.

Чтобы добавить задание для Cron для запуска, необходимо добавить задание в `crontab` файла. Чтобы открыть `crontab` файл в редакторе, где можно добавить или обновить задание, используйте следующую команду:

`crontab -e`

Задания было описано выше для выполнения ежедневно в 2:10, добавьте следующую строку в `crontab` файла:

```
# run SSIS package Name at 2:10AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Сохранить `crontab` файл и закройте редактор.

Чтобы понять формат пример команды, просмотрите сведения в следующем разделе.
 
## <a name="format-of-a-crontab-file"></a>Формат файла Crontab

На следующем рисунке показана описание формата строки задания, добавляемого `crontab` файла.

![Описание форматирования для записи в файл crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Чтобы получить более подробное описание `crontab` формат файла, используйте следующую команду:

`man 5 crontab`

Ниже приведен пример частичной выходных данных, которые помогут объяснить пример в этой статье:

![Подробное описание частичного crontab формата](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

