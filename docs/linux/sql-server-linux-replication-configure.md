---
title: Настройка репликации (SSMS)
description: В этой статье описывается настройка репликации SQL Server в Linux.
ms.custom: seo-dt-2019
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
titleSuffix: SQL Server on Linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0979f05808c59336dec7a6e4a664b2e970029dd6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75952498"
---
# <a name="configure-sql-server-replication-on-linux"></a>Настройка репликации SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В версии [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] реализована возможность репликации SQL Server для экземпляров SQL Server на Linux.

Дополнительные сведения о репликации см. в разделе [Документация по репликации SQL Server](../relational-databases/replication/sql-server-replication.md).

Для настройки репликации в Linux используйте хранимые процедуры SQL Server Management Studio (SSMS) или Transact-SQL.

* Чтобы использовать SSMS, следуйте инструкциям в этой статье.

  Используйте SSMS в операционной системе Windows для подключения к экземплярам SQL Server. Общие сведения и инструкции см. в разделе [Управление SQL Server на Linux с помощью SSMS](./sql-server-linux-manage-ssms.md).
  
* Пример с использованием хранимых процедур см. в руководстве [Настройка репликации SQL Server в Linux](sql-server-linux-replication-tutorial-tsql.md).

## <a name="prerequisites"></a>Предварительные требования

Прежде чем настраивать издателей, распространителей и подписчиков, необходимо задать определенную конфигурацию для экземпляра SQL Server.

1. Включите агент SQL Server, чтобы использовать агенты репликации. На всех серверах с Linux выполните следующие команды в терминале.

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
  sudo systemctl restart mssql-server
  ```

1. Настройте экземпляр SQL Server для репликации. Чтобы настроить экземпляр SQL Server для репликации, выполните команду `sys.sp_MSrepl_createdatatypemappings` на всех экземплярах, участвующих в репликации.

  ```sql
  USE msdb
  GO
  exec sys.sp_MSrepl_createdatatypemappings;
  GO
  ```

1. Создайте папку моментального снимка. Агенты SQL Server используют эту папку моментального снимка для чтения и записи. Создайте папку моментальных снимков на распространителе.

  Чтобы создать папку моментальных снимков и предоставить доступ пользователю `mssql`, выполните следующую команду:

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

## <a name="configure-and-monitor-replication-with-sql-server-management-studio-ssms"></a>Настройка и отслеживание репликации с помощью SQL Server Management Studio (SSMS)

### <a name="configure-the-distributor"></a>Настройка распространителя
  
Настройка распространителя: 

1. В SSMS установите подключение к экземпляру SQL Server в обозревателе объектов.

1. Щелкните правой кнопкой мыши элемент **Репликация** и выберите пункт **Настройка распространения**.

1. Выполните инструкции в **мастере настройки распространителя**.

### <a name="create-publication-and-articles"></a>Создание публикаций и статей

Создание публикаций и статей:

1. В обозревателе объектов щелкните правой кнопкой мыши **Репликация** > **Локальные публикации**> **Создать публикацию**.

1. Выполните инструкции в **мастере создания публикации**, чтобы настроить тип публикации, а также принадлежащие ей статьи.

### <a name="configure-the-subscription"></a>Настройка подписки

Чтобы настроить подписку, в обозревателе объектов щелкните **Репликация** > **Локальные подписки**> **Новые подписки**.

### <a name="monitor-replication-jobs"></a>Отслеживание заданий репликации

Для отслеживания заданий репликации используется монитор репликации.

В обозревателе объектов щелкните правой кнопкой мыши **Репликация** и выберите **Запустить монитор репликации**.

## <a name="next-steps"></a>Дальнейшие действия

[Основные понятия. Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).
