---
title: Параметры конфигурации сервера (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 02/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- surface area configuration [SQL Server], sp_configure
- configuration options [SQL Server], when take effect
- server management [SQL Server], configuration options
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], configuring
- configuration options [SQL Server], setting
- options [SQL Server], configuration
- RECONFIGURE statement
- performance [SQL Server], servers
- configuration options [SQL Server]
- RECONFIGURE WITH OVERRIDE statement
- SQL Server, configuring
- sp_configure
- stored procedures [SQL Server], configuration options
- server configuration [SQL Server]
- administering SQL Server, configuration options
ms.assetid: 9f38eba6-39b1-4f1d-ba24-ee4f7e2bc969
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 645aee1374f7dbf3c290500bb35ca47115983670
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62809572"
---
# <a name="server-configuration-options-sql-server"></a>Параметры конфигурации сервера (SQL Server)
  Управление и оптимизация ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производятся на основе параметров конфигурации с применением среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или системной хранимой процедуры sp_configure. Наиболее часто используемые параметры конфигурации сервера доступны в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]; доступ ко всем параметрам конфигурации можно получить при помощи sp_configure. Взвесьте возможные последствия для системы, прежде чем устанавливать эти параметры. Дополнительные сведения см. в разделе [Просмотр или изменение свойств сервера (SQL Server)](view-or-change-server-properties-sql-server.md).  
  
> [!IMPORTANT]  
>  Дополнительные параметры должны изменяться только опытным администратором баз данных или сертифицированным техническим специалистом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="categories-of-configuration-options"></a>Категории параметров конфигурации  
 Параметры конфигурации могут вступать в силу:  
  
-   немедленно после установки параметра и выполнения инструкции RECONFIGURE (или, в некоторых случаях, RECONFIGURE WITH OVERRIDE)  
  
     -или-  
  
-   После выполнения вышеуказанных действий и перезапуска экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Измененные значения параметров, требующих перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , первоначально будут отображены только в столбце value. После перезапуска новое значение отобразится в обоих столбцах, value и value_in_use.  
  
 Для некоторых параметров требуется перезапуск сервера прежде, чем новое конфигурационное значение вступит в силу. Если задано новое значение и выполнена процедура sp_configure перед перезапуском сервера, то новое значение появится в столбце value, но не в столбце value_in_use параметров конфигурации. После перезапуска сервера новое значение отобразится в столбце value_in_use.  
  
 Самонастраивающиеся параметры — это те, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] изменяет в соответствии с потребностями системы. В большинстве случаев это позволяет избавиться от необходимости устанавливать значения вручную. К примерам этого относятся параметры min server memory и max server memory, а также параметр user connections.  
  
## <a name="configuration-options-table"></a>Таблица параметров конфигурации  
 В нижеследующей таблице приведены все доступные параметры конфигурации, диапазон возможных значений и значения по умолчанию. Параметры конфигурации помечаются буквенными кодовыми обозначениями, как показано ниже:  
  
-   A= Дополнительные параметры, которые следует изменять только с помощью опытного администратора баз данных или сертифицированного технического специалиста [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и для которых требуется установить для show advanced options значение 1.  
  
-   RR = Параметры, требующие перезапуска компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   SC = Самонастраивающиеся параметры.  
  
    |Параметр конфигурации|Минимальное значение|Максимальное значение|Значение по умолчанию|  
    |--------------------------|-------------------|-------------------|-------------|  
    |[access check cache bucket count](access-check-cache-server-configuration-options.md) (A)|0|16384|0|  
    |[access check cache quota](access-check-cache-server-configuration-options.md) (A)|0|2147483647|0|  
    |[ad hoc distributed queries](ad-hoc-distributed-queries-server-configuration-option.md) (A)|0|1|0|  
    |[affinity I/O mask](affinity-input-output-mask-server-configuration-option.md) (A, RR)|-2147483648|2147483647|0|  
    |[affinity64 I/O mask](affinity64-input-output-mask-server-configuration-option.md) (A, доступно только в 64-разрядной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])|-2147483648|2147483647|0|  
    |[affinity mask](affinity-mask-server-configuration-option.md) (A)|-2147483648|2147483647|0|  
    |[affinity64 mask](affinity64-mask-server-configuration-option.md) (A, RP), доступно только в 64-разрядной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|-2147483648|2147483647|0|  
    |[Agent XPs](agent-xps-server-configuration-option.md) (A)|0|1|0<br /><br /> (Изменяется на 1, если запускается агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; Значение по умолчанию равно 0, если при установке был указан автоматический запуск агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .)|  
    |[allow updates](allow-updates-server-configuration-option.md) (Устаревший. Не используйте. Вызовет ошибку во время повторной настройки.)|0|1|0|  
    |[Контрольная сумма резервной копии: значение по умолчанию](../backup-checksum-default.md)|0|1|0|  
    |[backup compression default](view-or-configure-the-backup-compression-default-server-configuration-option.md)|0|1|0|  
    |[blocked process threshold](blocked-process-threshold-server-configuration-option.md) (A)|0|86400|0|  
    |[c2 audit mode](c2-audit-mode-server-configuration-option.md) (A, RR)|0|1|0|  
    |[clr enabled](clr-enabled-server-configuration-option.md)|0|1|0|  
    |[common criteria compliance enabled](common-criteria-compliance-enabled-server-configuration-option.md) (A, RR)|0|1|0|  
    |[Проверка подлинности автономной базы данных](contained-database-authentication-server-configuration-option.md)|0||0|  
    |[cost threshold for parallelism](configure-the-cost-threshold-for-parallelism-server-configuration-option.md) (A)|0|32767|5|  
    |[cross db ownership chaining](cross-db-ownership-chaining-server-configuration-option.md)|0|1|0|  
    |[cursor threshold](configure-the-cursor-threshold-server-configuration-option.md) (A)|-1|2147483647|-1|  
    |[Database Mail XPs](database-mail-xps-server-configuration-option.md) (A)|0|1|0|  
    |[default full-text language](configure-the-default-full-text-language-server-configuration-option.md) (A)|0|2147483647|1033|  
    |[язык по умолчанию](configure-the-default-language-server-configuration-option.md)|0|9999|0|  
    |[default trace enabled](default-trace-enabled-server-configuration-option.md) (A)|0|1|1|  
    |[disallow results from triggers](disallow-results-from-triggers-server-configuration-option.md) (A)|0|1|0|  
    |[Поставщик расширенного управления ключами включен](ekm-provider-enabled-server-configuration-option.md)|0|1|0|  
    |[filestream_access_level](filestream-access-level-server-configuration-option.md)|0|2|0|  
    |[fill factor](configure-the-fill-factor-server-configuration-option.md) (A, RR)|0|100|0|  
    |ft crawl bandwidth (max), см. раздел [ft crawl bandwidth](ft-crawl-bandwidth-server-configuration-option.md)(A)|0|32767|100|  
    |ft crawl bandwidth (min), см. раздел [ft crawl bandwidth](ft-crawl-bandwidth-server-configuration-option.md)(A)|0|32767|0|  
    |ft notify bandwidth (max), см. раздел [ft notify bandwidth](ft-notify-bandwidth-server-configuration-option.md)(A)|0|32767|100|  
    |ft notify bandwidth (min), см. раздел [ft notify bandwidth](ft-notify-bandwidth-server-configuration-option.md)(A)|0|32767|0|  
    |[index create memory](configure-the-index-create-memory-server-configuration-option.md) (A, SC)|704|2147483647|0|  
    |[in-doubt xact resolution](in-doubt-xact-resolution-server-configuration-option.md) (A)|0|2|0|  
    |[lightweight pooling](lightweight-pooling-server-configuration-option.md) (A, RR)|0|1|0|  
    |[locks](configure-the-locks-server-configuration-option.md) (A, RR, SC)|5000|2147483647|0|  
    |[max degree of parallelism](configure-the-max-degree-of-parallelism-server-configuration-option.md) (A)|0|32767|0|  
    |[max full-text crawl range](max-full-text-crawl-range-server-configuration-option.md) (A)|0|256|4|  
    |[max server memory](server-memory-server-configuration-options.md) (A, SC)|16|2147483647|2147483647|  
    |[max text repl size](configure-the-max-text-repl-size-server-configuration-option.md)|0|2147483647|65536|  
    |[max worker threads](configure-the-max-worker-threads-server-configuration-option.md) (A)|128|32767<br /><br /> (1024 является максимальным значением, рекомендуемым для 32-разрядных операционных систем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 2048 — для 64-разрядных систем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)|0<br /><br /> При нулевом значении максимальное число рабочих потоков исполнителя настраивается автоматически в зависимости от количества процессоров по формуле (256 + ( *\<процессоры>* - 4) * 8) для 32-разрядных систем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и в два раза больше для 64-разрядных систем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
    |[media retention](configure-the-media-retention-server-configuration-option.md) (A, RR)|0|365|0|  
    |[min memory per query](configure-the-min-memory-per-query-server-configuration-option.md) (A)|512|2147483647|1024|  
    |[min server memory](server-memory-server-configuration-options.md) (A, SC)|0|2147483647|0|  
    |[вложенные триггеры](configure-the-nested-triggers-server-configuration-option.md)|0|1|1|  
    |[network packet size](configure-the-network-packet-size-server-configuration-option.md) (A)|512|32767|4096|  
    |[Ole Automation Procedures](ole-automation-procedures-server-configuration-option.md) (A)|0|1|0|  
    |[open objects](open-objects-server-configuration-option.md) (A, RR, устаревший)|0|2147483647|0|  
    |[optimize for ad hoc workloads](optimize-for-ad-hoc-workloads-server-configuration-option.md) (A)|0|1|0|  
    |[PH_timeout](ph-timeout-server-configuration-option.md) (A)|1|3600|60|  
    |[precompute rank](precompute-rank-server-configuration-option.md) (A)|0|1|0|  
    |[priority boost](configure-the-priority-boost-server-configuration-option.md) (A, RR)|0|1|0|  
    |[query governor cost limit](configure-the-query-governor-cost-limit-server-configuration-option.md) (A)|0|2147483647|0|  
    |[query wait](configure-the-query-wait-server-configuration-option.md) (A)|-1|2147483647|-1|  
    |[recovery interval](configure-the-recovery-interval-server-configuration-option.md) (A, SC)|0|32767|0|  
    |[remote access](configure-the-remote-access-server-configuration-option.md) (RR)|0|1|1|  
    |[remote admin connections](remote-admin-connections-server-configuration-option.md)|0|1|0|  
    |[remote login timeout](configure-the-remote-login-timeout-server-configuration-option.md)|0|2147483647|10|  
    |[remote proc trans](configure-the-remote-proc-trans-server-configuration-option.md)|0|1|0|  
    |[remote query timeout](configure-the-remote-query-timeout-server-configuration-option.md)|0|2147483647|600|  
    |[Replication XPs Option](replication-xps-server-configuration-option.md) (A)|0|1|0|  
    |[scan for startup procs](configure-the-scan-for-startup-procs-server-configuration-option.md) (A, RR)|0|1|0|  
    |[server trigger recursion](server-trigger-recursion-server-configuration-option.md)|0|1|1|  
    |[set working set size](set-working-set-size-server-configuration-option.md) (A, RR, устаревший)|0|1|0|  
    |[show advanced options](show-advanced-options-server-configuration-option.md)|0|1|0|  
    |[SMO and DMO XPs](smo-and-dmo-xps-server-configuration-option.md) (A)|0|1|1|  
    |[transform noise words](transform-noise-words-server-configuration-option.md) (A)|0|1|0|  
    |[two digit year cutoff](configure-the-two-digit-year-cutoff-server-configuration-option.md) (A)|1753|9999|2049|  
    |[user connections](configure-the-user-connections-server-configuration-option.md) (A, RR, SC)|0|32767|0|  
    |[user options](configure-the-user-options-server-configuration-option.md)|0|32767|0|  
    |[xp_cmdshell](xp-cmdshell-server-configuration-option.md) (A)|0|1|0|  
  
## <a name="see-also"></a>См. также  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
