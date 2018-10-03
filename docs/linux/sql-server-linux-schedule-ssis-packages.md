---
title: Планирование пакетов служб SSIS в Linux с помощью cron | Документация Майкрософт
description: В этой статье описывается планирование пакетов служб SQL Server Integration Services (SSIS) на платформе Linux с помощью службы cron.
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: bfc30c25d93581ee36f88c075416dbfebf59aea1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753502"
---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>Расписание SQL Server Integration Services выполнения пакета в Linux с помощью cron

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

При запуске службы SQL Server Integration Services (SSIS) и SQL Server на Windows, можно автоматизировать выполнение пакетов служб SSIS с помощью агента SQL Server. Тем не менее, при запуске SQL Server и служб SSIS в Linux, служебную программу агента SQL Server недоступна планировать задания в Linux. Вместо этого использовать службы cron, которое широко используется на платформах Linux для автоматизации выполнения пакета.

В этой статье приведены примеры, показано, как автоматизировать выполнение пакетов служб SSIS. Примеры написаны под управлением Red Hat Enterprise. Код аналогичен и для других дистрибутивов Linux, таких как Ubuntu.

## <a name="prerequisites"></a>предварительные требования

Прежде чем использовать службы cron для выполнения заданий, проверьте, выполняется ли он на компьютере.

Чтобы проверить состояние службы cron, используйте следующую команду: `systemctl status crond.service`.

Если служба не активна (то есть он не работает), обратитесь к администратору, чтобы установить и настроить службы cron должным образом.

## <a name="create-jobs"></a>Создание заданий

Задания cron — это задача, можно настроить для регулярного выполнения с заданным интервалом. Задание может быть сложнее, чем команды, которая бы обычно введите непосредственно в консоли и выполнять как сценарий оболочки.

Для упрощения управления и обслуживания рекомендуется размещать ваши команды выполнения пакета в скрипт, содержащий описательное имя.

Ниже приведен пример простой сценарий запуска пакета. Он содержит только одну команду, но при необходимости можно добавить дополнительные команды.

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Планирование заданий с помощью службы cron

После определения заданий, можно запланировать их автоматический запуск с помощью службы cron.

Чтобы добавить задание для cron для запуска, добавьте задание в файле crontab. Чтобы открыть файл crontab в редакторе, где можно добавить или обновить задание, используйте следующую команду: `crontab -e`.

Для задания ранее описанных ежедневно в 2:10, добавьте следующую строку в файл crontab:

```
# run <SSIS package name> at 2:10 AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Сохраните файл crontab и закройте редактор.

Чтобы понять формат пример команды, просмотрите сведения в следующем разделе.
 
## <a name="format-of-a-crontab-file"></a>Формат файла crontab

Ниже приведен формат Описание строки задания, который добавляется в файл crontab.

![Описание формата для записи в файле crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Чтобы получить более подробное описание формата файла crontab, используйте следующую команду: `man 5 crontab`.

Ниже приведен неполный пример выходных данных, которые помогут объяснить, в примере в этой статье:

![Подробное описание частичного crontab формата](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

## <a name="related-content-about-ssis-on-linux"></a>См. также сведения о службах SSIS на платформе Linux
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Установка SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Настройка SQL Server Integration Services в Linux с помощью служб ssis-conf](sql-server-linux-configure-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
