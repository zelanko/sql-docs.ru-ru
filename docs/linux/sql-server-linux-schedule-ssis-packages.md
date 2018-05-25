---
title: Расписание выполнения пакетов служб SSIS в Linux с cron | Документы Microsoft
description: В этой статье описан процесс составления расписания пакеты служб SQL Server Integration Services (SSIS) для Linux с службы cron.
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 3dd2c69dae65f073ec7bc34a40ae1f31be2c1a7c
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>Выполнение в Linux с cron пакетов служб интеграции SQL Server расписание

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

При работе с SQL Server Integration Services (SSIS) и SQL Server в Windows, можно автоматизировать выполнение пакетов служб SSIS с помощью агента SQL Server. При работе с SQL Server и служб SSIS в Linux, служебную программу агента SQL Server недоступен, расписание заданий в Linux. Вместо этого использовать службы cron, которая широко применяется для платформ Linux для автоматизации выполнения пакета.

Эта статья содержит примеры, которые показывают, как автоматизировать выполнение пакетов служб SSIS. Примеры предназначены для запуска в Red Hat Enterprise. Для других дистрибутивов Linux, например Ubuntu аналогично код.

## <a name="prerequisites"></a>предварительные требования

Прежде чем использовать службы cron для выполнения заданий, проверьте, выполняется ли он на вашем компьютере.

Чтобы проверить состояние службы cron, используйте следующую команду: `systemctl status crond.service`.

Если служба не активна (то есть, он не работает), обратитесь к администратору, чтобы установить и настроить службы cron должным образом.

## <a name="create-jobs"></a>Создание задания

Задание cron — задачи, которые можно настроить регулярное выполнение с заданным интервалом. Задание может быть простым как команду, которая обычно бы ввести непосредственно в консоль или запуска от имени сценария оболочки.

Для упрощения управления и выполнения задач технического обслуживания рекомендуется поместить команды выполнения пакета в скрипт, содержащий описательное имя.

Ниже приведен пример простой сценарий для запуска пакета. Он содержит только одну команду, но при необходимости можно добавить дополнительные команды.

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Планирование заданий в службе cron

После определения заданий, можно запланировать их автоматический запуск с помощью службы cron.

Чтобы добавить задание для cron для запуска, добавьте задание в файле crontab. Чтобы открыть файл crontab в редакторе, где можно добавить или обновить задание, используйте следующую команду: `crontab -e`.

Чтобы запланировать задание описано выше, чтобы выполнять ежедневно в 2:10:00, добавьте следующую строку в файл crontab:

```
# run <SSIS package name> at 2:10 AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Сохраните файл crontab, а затем закройте редактор.

Чтобы понять формат пример команды, просмотрите сведения в следующем разделе.
 
## <a name="format-of-a-crontab-file"></a>Формат файла crontab

Ниже приведен описание формата строки добавляется в файл crontab работы.

![Описание форматирования для записи в файл crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Чтобы получить более подробное описание формата файла crontab, используйте следующую команду: `man 5 crontab`.

Ниже приведен пример частичной выходных данных, которые помогут объяснить пример в этой статье:

![Подробное описание частичного crontab формата](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

## <a name="related-content-about-ssis-on-linux"></a>См. также о служб SSIS в Linux
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Установка SQL Server Integration Services (SSIS) для Linux](sql-server-linux-setup-ssis.md)
-   [Настройка служб интеграции SQL Server в Linux с conf служб ssis](sql-server-linux-configure-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
