---
title: Планирование пакетов SSIS в Linux с помощью cron
description: В этой статье приводятся инструкции по планированию пакетов служб SQL Server Integration Services (SSIS) в Linux с помощью службы cron.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: ac7648287b4e4b609f4dd4f25b1b07a512065364
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68065160"
---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>Планирование выполнения пакетов SQL Server Integration Services в Linux с помощью cron

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

При запуске SQL Server Integration Services (SSIS) и SQL Server в Windows можно автоматизировать выполнение пакетов SSIS с помощью агента SQL Server. Однако при запуске SQL Server и служб SSIS в Linux служебная программа агента SQL Server недоступна для планирования заданий в Linux. Вместо этого для автоматизации выполнения пакетов используется служба cron, которая получила широкое распространение на платформах Linux.

В этой статье приведены примеры, демонстрирующие автоматизацию выполнения пакетов SSIS. Эти примеры написаны для запуска в Red Hat Enterprise. Аналогичный код используется для других дистрибутивов Linux, таких как Ubuntu.

## <a name="prerequisites"></a>предварительные требования

Прежде чем использовать службу cron для запуска заданий, проверьте, запущена ли она на компьютере.

Чтобы проверить состояние службы cron, используйте следующую команду: `systemctl status crond.service`.

Если служба неактивна (т. е. не запущена), обратитесь к администратору, чтобы правильно настроить и настроить службу cron.

## <a name="create-jobs"></a>Создание заданий

Задание cron — это задача, которую можно настроить для регулярного запуска с заданным интервалом. Это задание может быть простым, как команда, которая обычно вводится непосредственно в консоли или запускается как скрипт оболочки.

Для простоты управления и обслуживания рекомендуется поместить команды выполнения пакета в скрипт, имеющий описательное имя.

Ниже приведен пример простого скрипта оболочки для запуска пакета. Он содержит только одну команду, но при необходимости можно добавить дополнительные команды.

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Планирование заданий с помощью службы cron

После определения заданий можно запланировать их автоматический запуск с помощью службы cron.

Чтобы добавить задание для выполнения cron, добавьте его в файл crontab. Чтобы открыть файл crontab в редакторе, где можно добавить или обновить задание, используйте следующую команду: `crontab -e`.

Чтобы запланировать выполнение ранее описанного задания ежедневно в 2:10, добавьте в файл crontab следующую строку.

```
# run <SSIS package name> at 2:10 AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Сохраните файл crontab и закройте редактор.

Чтобы понять формат примера команды, ознакомьтесь со сведениями в следующем разделе.
 
## <a name="format-of-a-crontab-file"></a>Формат файла crontab

На следующем изображении показано описание формата для строки задания, добавленной в файл crontab.

![Описание формата записи в файле crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Чтобы получить более подробное описание формата файла crontab, используйте следующую команду: `man 5 crontab`.

Ниже приведен частичный пример выходных данных, которые помогут объяснить пример в этой статье.

![Подробное частичное описание формата crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

## <a name="related-content-about-ssis-on-linux"></a>Связанные материалы о службах SSIS в Linux
-   [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Установка служб SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Настройка SQL Server Integration Services в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
