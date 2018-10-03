---
title: Настройка репликации SQL Server в Linux | Документация Майкрософт
description: В этой статье описывается, как настроить репликацию SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 58cbcb648d6318b1b013082fc621c48e278f9186
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793582"
---
# <a name="configure-sql-server-replication-on-linux"></a>Настройка репликации SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Представляет репликации SQL Server для экземпляров SQL Server в Linux.

Подробные сведения о репликации см. в разделе [руководство по репликации SQL Server](../relational-databases/replication/sql-server-replication.md).

Настройка репликации на платформе Linux с помощью SQL Server Management Studio (SSMS), или Transact-SQL хранимой процедуры.

* Чтобы использовать SSMS, следуйте инструкциям в этой статье.

  Для подключения к экземплярам SQL Server с помощью SSMS в операционной системе Windows. Фона и инструкции, см. в разделе [используйте SSMS для управления SQL Server в Linux](./sql-server-linux-manage-ssms.md).
  
* Пример с помощью хранимых процедур, выполните [репликации SQL Server можно настроить на платформе Linux](sql-server-linux-replication-tutorial-tsql.md) руководства.

## <a name="prerequisites"></a>предварительные требования

Прежде чем настраивать издателей, распространителей и подписчиков, необходимо выполнить ряд действия по настройке для экземпляра SQL Server.

1. Включите агент SQL Server для использования агентов репликации. На всех серверах Linux выполните следующие команды в окне терминала.

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
  sudo systemctl restart mssql-server
  ```

1. Настройте экземпляр SQL Server для репликации. Чтобы настроить экземпляр SQL Server для репликации, запустите `sys.sp_MSrepl_createdatatypemappings` на всех экземплярах, участвующих в репликации.

  ```sql
  USE msdb
  GO
  exec sys.sp_MSrepl_createdatatypemappings;
  GO
  ```

1. Создайте папку моментальных снимков. Агенты SQL Server требуется на чтение и запись для папки моментальных снимков. Создайте папку моментальных снимков на распространителе.

  Чтобы создать папку моментальных снимков и предоставить доступ к `mssql` пользователя, выполните следующую команду:

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

## <a name="configure-and-monitor-replication-with-sql-server-management-studio-ssms"></a>Настройки и наблюдения за репликацией с помощью SQL Server Management Studio (SSMS)

### <a name="configure-the-distributor"></a>Настройка распространителя
  
Для настройки распространителя: 

1. В среде SSMS подключитесь к экземпляру SQL Server в обозревателе объектов.

1. Щелкните правой кнопкой мыши **репликации**и нажмите кнопку **настроить распространение...** .

1. Следуйте инструкциям на **мастера настройки распространителя**.

### <a name="create-publication-and-articles"></a>Создание публикации и статьи

Для создания, публикации и статьи:

1. В обозревателе объектов щелкните **репликации** > **Локальные публикации**> **новой публикации...** .

1. Следуйте инструкциям на **мастера создания публикаций** для настройки типа репликации и статей, относящихся к публикации.

### <a name="configure-the-subscription"></a>Настройка подписки

Чтобы настроить подписку, в обозревателе объектов, щелкните **репликации** > **Локальные подписки**> **новые подписки...** .

### <a name="monitor-replication-jobs"></a>Мониторинг заданий репликации

Использование монитора репликации для отслеживания заданий репликации.

В обозревателе объектов щелкните правой кнопкой мыши **репликации**и нажмите кнопку **запустить монитор репликации**.

## <a name="next-steps"></a>Следующие шаги

[Основные понятия: Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).
