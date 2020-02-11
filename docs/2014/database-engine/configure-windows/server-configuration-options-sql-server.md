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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809572"
---
# <a name="server-configuration-options-sql-server"></a>Параметры конфигурации сервера (SQL Server)
  Управление и оптимизация ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производятся на основе параметров конфигурации с применением среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или системной хранимой процедуры sp_configure. Наиболее часто используемые параметры конфигурации сервера доступны в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]; доступ ко всем параметрам конфигурации можно получить при помощи sp_configure. Взвесьте возможные последствия для системы, прежде чем устанавливать эти параметры. Дополнительные сведения см. в разделе [Просмотр или изменение свойств сервера (SQL Server)](view-or-change-server-properties-sql-server.md).  
  
> [!IMPORTANT]  
>  Дополнительные параметры должны изменяться только опытным администратором баз данных или сертифицированным техническим специалистом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
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
  
    |Параметр конфигурации|Минимальное значение|Максимальное значение|По умолчанию|  
    |--------------------------|-------------------|-------------------|-------------|  
    |[доступ к счетчику контейнеров проверки кэша](access-check-cache-server-configuration-options.md) (A)|0|16 384|0|  
    |[доступ к квоте кэша проверки](access-check-cache-server-configuration-options.md) (а)|0|2147483647|0|  
    |[Нерегламентированные распределенные запросы](ad-hoc-distributed-queries-server-configuration-option.md) (A)|0|1|0|  
    |[сходство масок ввода-вывода](affinity-input-output-mask-server-configuration-option.md) (A, RR)|-2147483648|2147483647|0|  
    |[affinity64ная маска ввода-вывода](affinity64-input-output-mask-server-configuration-option.md) (A, доступна только в 64-разрядной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]версии)|-2147483648|2147483647|0|  
    |[маска сходства](affinity-mask-server-configuration-option.md) (A)|-2147483648|2147483647|0|  
    |[Маска affinity64](affinity64-mask-server-configuration-option.md) (A, RR) доступна только в 64-разрядной версии[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|-2147483648|2147483647|0|  
    |[Агент XPS](agent-xps-server-configuration-option.md) (A)|0|1|0<br /><br /> (Изменяется на 1, если запускается агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; Значение по умолчанию равно 0, если при установке был указан автоматический запуск агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .)|  
    |[Разрешить обновления](allow-updates-server-configuration-option.md) (устаревшие. Не используйте. Вызовет ошибку во время повторной настройки.)|0|1|0|  
    |[Контрольная сумма резервной копии: значение по умолчанию](../backup-checksum-default.md)|0|1|0|  
    |[backup compression default](view-or-configure-the-backup-compression-default-server-configuration-option.md)|0|1|0|  
    |[пороговое значение заблокированного процесса](blocked-process-threshold-server-configuration-option.md) (A)|0|86400|0|  
    |[режим аудита C2](c2-audit-mode-server-configuration-option.md) (A, RR)|0|1|0|  
    |[clr enabled](clr-enabled-server-configuration-option.md)|0|1|0|  
    |[соответствие стандарту Common условия_отбора включено](common-criteria-compliance-enabled-server-configuration-option.md) (a, RR)|0|1|0|  
    |[Проверка подлинности автономной базы данных](contained-database-authentication-server-configuration-option.md)|0||0|  
    |[пороговое значение стоимости для параллелизма](configure-the-cost-threshold-for-parallelism-server-configuration-option.md) (A)|0|32767|5|  
    |[cross db ownership chaining](cross-db-ownership-chaining-server-configuration-option.md)|0|1|0|  
    |[пороговое значение курсора](configure-the-cursor-threshold-server-configuration-option.md) (A)|-1|2147483647|-1|  
    |[Database Mail XPS](database-mail-xps-server-configuration-option.md) (A)|0|1|0|  
    |[язык полнотекстового текста по умолчанию](configure-the-default-full-text-language-server-configuration-option.md) (A)|0|2147483647|1033|  
    |[язык по умолчанию](configure-the-default-language-server-configuration-option.md)|0|9999|0|  
    |[Трассировка по умолчанию включена](default-trace-enabled-server-configuration-option.md) (A)|0|1|1|  
    |[запретить результаты триггеров](disallow-results-from-triggers-server-configuration-option.md) (A)|0|1|0|  
    |[Поставщик расширенного управления ключами включен](ekm-provider-enabled-server-configuration-option.md)|0|1|0|  
    |[filestream_access_level](filestream-access-level-server-configuration-option.md)|0|2|0|  
    |[Коэффициент заполнения](configure-the-fill-factor-server-configuration-option.md) (A, RR)|0|100|0|  
    |ft crawl bandwidth (max), см. раздел [ft crawl bandwidth](ft-crawl-bandwidth-server-configuration-option.md)(A)|0|32767|100|  
    |ft crawl bandwidth (min), см. раздел [ft crawl bandwidth](ft-crawl-bandwidth-server-configuration-option.md)(A)|0|32767|0|  
    |ft notify bandwidth (max), см. раздел [ft notify bandwidth](ft-notify-bandwidth-server-configuration-option.md)(A)|0|32767|100|  
    |ft notify bandwidth (min), см. раздел [ft notify bandwidth](ft-notify-bandwidth-server-configuration-option.md)(A)|0|32767|0|  
    |[память для создания индекса](configure-the-index-create-memory-server-configuration-option.md) (A, SC)|704|2147483647|0|  
    |[Разрешение проблемных транзакций](in-doubt-xact-resolution-server-configuration-option.md) (A)|0|2|0|  
    |использование [упрощенных пулов](lightweight-pooling-server-configuration-option.md) (a, RR)|0|1|0|  
    |[блокировки](configure-the-locks-server-configuration-option.md) (A, RR, SC)|5000|2147483647|0|  
    |[Максимальная степень параллелизма](configure-the-max-degree-of-parallelism-server-configuration-option.md) (A)|0|32767|0|  
    |[максимальный диапазон полнотекстового сканирования](max-full-text-crawl-range-server-configuration-option.md) (A)|0|256|4|  
    |[максимальный объем памяти сервера](server-memory-server-configuration-options.md) (A, SC)|16|2147483647|2147483647|  
    |[max text repl size](configure-the-max-text-repl-size-server-configuration-option.md)|0|2147483647|65536|  
    |[Максимальное число рабочих потоков](configure-the-max-worker-threads-server-configuration-option.md) (A)|128|32767<br /><br /> (1024 является максимальным значением, рекомендуемым для 32-разрядных операционных систем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 2048 — для 64-разрядных систем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)|0<br /><br /> При нулевом значении максимальное число рабочих потоков не настраивается в зависимости от числа процессоров, с использованием формулы (256 + (*\<процессоры>* -4) * 8) для 32 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -бит и дважды для 64- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]бит.|  
    |[Хранение носителей](configure-the-media-retention-server-configuration-option.md) (A, RR)|0|365|0|  
    |[Минимальный объем памяти на запрос](configure-the-min-memory-per-query-server-configuration-option.md) (A)|512|2147483647|1024|  
    |[min server memory](server-memory-server-configuration-options.md) (A, SC)|0|2147483647|0|  
    |[вложенные триггеры](configure-the-nested-triggers-server-configuration-option.md)|0|1|1|  
    |[Размер сетевого пакета](configure-the-network-packet-size-server-configuration-option.md) (A)|512|32767|4096|  
    |[Процедуры OLE-автоматизации](ole-automation-procedures-server-configuration-option.md) (A)|0|1|0|  
    |[открытые объекты](open-objects-server-configuration-option.md) (A, RR, устаревшие)|0|2147483647|0|  
    |[оптимизировать для нерегламентированных рабочих нагрузок](optimize-for-ad-hoc-workloads-server-configuration-option.md) (A)|0|1|0|  
    |[PH_timeout](ph-timeout-server-configuration-option.md) (A)|1|3600|60|  
    |[предварительное вычисление ранга](precompute-rank-server-configuration-option.md) (A)|0|1|0|  
    |[повышение приоритета](configure-the-priority-boost-server-configuration-option.md) (A, RR)|0|1|0|  
    |[ограничение стоимости регулятора запросов](configure-the-query-governor-cost-limit-server-configuration-option.md) (A)|0|2147483647|0|  
    |[Ожидание запроса](configure-the-query-wait-server-configuration-option.md) (а)|-1|2147483647|-1|  
    |[интервал восстановления](configure-the-recovery-interval-server-configuration-option.md) (A, SC)|0|32767|0|  
    |[Удаленный доступ](configure-the-remote-access-server-configuration-option.md) (RR)|0|1|1|  
    |[remote admin connections](remote-admin-connections-server-configuration-option.md)|0|1|0|  
    |[время ожидания удаленного входа](configure-the-remote-login-timeout-server-configuration-option.md)|0|2147483647|10|  
    |[remote proc trans](configure-the-remote-proc-trans-server-configuration-option.md)|0|1|0|  
    |[remote query timeout](configure-the-remote-query-timeout-server-configuration-option.md)|0|2147483647|600|  
    |[Параметр репликации XPS](replication-xps-server-configuration-option.md) (A)|0|1|0|  
    |[Проверка на наличие процедур запуска](configure-the-scan-for-startup-procs-server-configuration-option.md) (A, RR)|0|1|0|  
    |[server trigger recursion](server-trigger-recursion-server-configuration-option.md)|0|1|1|  
    |[задать размер рабочего набора](set-working-set-size-server-configuration-option.md) (A, RR, устаревший)|0|1|0|  
    |[show advanced options](show-advanced-options-server-configuration-option.md)|0|1|0|  
    |[SMO и DMO XPS](smo-and-dmo-xps-server-configuration-option.md) (A)|0|1|1|  
    |[Преобразование пропускаемых слов](transform-noise-words-server-configuration-option.md) (A)|0|1|0|  
    |[отсечение двух цифр года](configure-the-two-digit-year-cutoff-server-configuration-option.md) (A)|1753|9999|2049|  
    |[подключения пользователей](configure-the-user-connections-server-configuration-option.md) (A, RR, SC)|0|32767|0|  
    |[параметры пользователя](configure-the-user-options-server-configuration-option.md)|0|32767|0|  
    |[xp_cmdshell](xp-cmdshell-server-configuration-option.md) (A)|0|1|0|  
  
## <a name="see-also"></a>См. также:  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
