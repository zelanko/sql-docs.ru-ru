---
title: Настройка сжатия резервных копий (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 430905eb-d218-458c-bd48-aeee6fbb7446
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7136e9f5bda8cd873ae9d30c14ef66b6acf324ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287510"
---
# <a name="configure-backup-compression-sql-server"></a>Настройка сжатия резервных копий (SQL Server)
  При установке сжатие резервных копий по умолчанию отключено. По умолчанию способ сжатия резервных копий определяется параметром конфигурации **backup compression default** уровня сервера. Однако настройку по умолчанию на уровне сервера можно переопределить при создании отдельной резервной копии или во время планирования ряда регулярных операций резервного копирования. Чтобы изменить это параметр, см. раздел [Параметр конфигурации сервера "Просмотр или настройка параметра сжатия резервных копий по умолчанию"](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).  
  
## <a name="override-the-backup-compression-default"></a>Переопределение сжатия резервных копий по умолчанию  
 Способ сжатия резервных копий вы можете изменить для отдельной резервной копии, задания резервного копирования или для конфигурации доставки журналов.  
  
-   **[!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
     Для переопределения сжатия резервных копий по умолчанию используйте параметр WITH NO_COMPRESSION или WITH COMPRESSION в инструкции [BACKUP](/sql/t-sql/statements/backup-transact-sql) в процессе создания резервной копии.  
  
     Для конфигурации доставки журналов поведение сжатия резервных копий можно контролировать с помощью хранимой процедуры [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql).  
  
-   **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
     Сведения о просмотре или настройке параметра сжатия резервных копий по умолчанию для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Параметр конфигурации сервера "Просмотр или настройка параметра сжатия резервных копий по умолчанию"](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).  
  
     Можно переопределить сжатие резервных копий по умолчанию для сервера, выбрав **Сжимать резервные копии** или **Не сжимать резервные копии** в одном из следующих диалоговых окон:  
  
    -   [Резервное копирование базы данных (страница «Параметры»)](back-up-database-backup-options-page.md)  
  
         При резервном копировании базы данных можно управлять сжатием резервной копии для отдельной базы данных, файла или журнала.  
  
    -   [Использование мастера планов обслуживания](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
         Мастер планов обслуживания позволяет управлять сжатием резервных копий для каждого запланированного набора полных или разностных резервных копий базы данных или журнала.  
  
    -   Integration Services (SSIS) [Задача "Резервное копирование базы данных"](../../integration-services/control-flow/back-up-database-task.md)  
  
         Сжатием резервных копий можно управлять при создании пакета для резервного копирования отдельной базы данных или нескольких баз данных.  
  
    -   [Настройки резервного копирования журналов транзакций для доставки журналов](../databases/log-shipping-transaction-log-backup-settings.md)  
  
         Можно управлять поведением сжатия резервных копий журналов.  
  
  
## <a name="see-also"></a>См. также  
 [Сжатие резервных копий (SQL Server)](backup-compression-sql-server.md)  
  
  
