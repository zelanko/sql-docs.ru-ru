---
title: Приложение sqllogship | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqllogship
ms.assetid: 8ae70041-f3d9-46e4-8fa8-31088572a9f8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 14b9cda05bca998bd113a316692c4c2c2111d091
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035081"
---
# <a name="sqllogship-application"></a>Приложение sqllogship
  Приложение **sqllogship** выполняет операции резервного копирования, копирования и восстановления, а также связанные задачи очистки для конфигурации доставки журналов. Операция выполняется на определенном экземпляре [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для конкретной базы данных.  
  
 ![Значок ссылки на раздел](../../2014/database-engine/media/topic-link.gif "Значок ссылки на раздел") Сведения о синтаксических обозначениях см. в [справочнике по программе командной строки &#40;ядро СУБД&#41;](../tools/command-prompt-utility-reference-database-engine.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqllogship  
-server  
instance_name { -backupprimary_id | -copysecondary_id | -restoresecondary_id } [ -verboselevellevel ] [ -logintimeouttimeout_value ] [ -querytimeouttimeout_value ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **-server** _instance_name_  
 Указывает экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , где будет выполняться операция. Указываемый экземпляр сервера зависит от того, на каком сервере задается операция доставки журналов. Для операции **-backup**в качестве аргумента *имя_сервера* должно быть указано имя сервера-источника, заданное в конфигурации доставки журналов. Для операции **-copy** или **-restore**в качестве аргумента *имя_сервера* указывается имя сервера-получателя, заданное в конфигурации доставки журналов.  
  
 **-primary_id резервного копирования** __  
 Выполняет операцию резервного копирования для базы данных-источника, основной идентификатор которой определяется аргументом *primary_id*. Этот идентификатор можно получить из системной таблицы [log_shipping_primary_databases](/sql/relational-databases/system-tables/log-shipping-primary-databases-transact-sql) или хранимой процедурой [sp_help_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql) .  
  
 Операция резервного копирования создает резервную копию журналов в каталоге резервного копирования. Затем приложение **sqllogship** удаляет все старые файлы резервной копии на основе срока их хранения. Приложение записывает журнал для операции резервного копирования на сервер-источник и сервер мониторинга. Наконец, оно запускает хранимую процедуру [sp_cleanup_log_shipping_history](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql), которая удаляет старые данные в журнале на основе срока их хранения.  
  
 **-copy** _secondary_id_  
 Выполняет операцию копирования резервных копий с указанного сервера-получателя для базы данных-получателя или баз данных со вторичным идентификатором, указываемым аргументом *secondary_id*. Этот идентификатор можно получить из системной таблицы [log_shipping_secondary](/sql/relational-databases/system-tables/log-shipping-secondary-transact-sql) или хранимой процедурой [sp_help_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql) .  
  
 Операция выполняет копирование файлов резервной копии из каталога резервного копирования в целевой каталог. Затем приложение **sqllogship** записывает журнал для операции копирования на сервер-получатель и сервер мониторинга.  
  
 **— восстановление** _secondary_id_  
 Выполняет операцию восстановления на указанный сервер-получатель для базы данных-получателя или баз данных со вспомогательным идентификатором, указываемым аргументом *secondary_id*. Этот идентификатор можно получить хранимой процедурой **sp_help_log_shipping_secondary_database** .  
  
 Все файлы резервной копии в целевом каталоге, созданные после самой последней точки восстановления, восстанавливаются в базы данных-получатели. Затем приложение **sqllogship** удаляет все старые файлы резервной копии на основе срока их хранения. Приложение записывает журнал для операции восстановления на сервер-получатель и сервер мониторинга. Наконец, оно запускает хранимую процедуру **sp_cleanup_log_shipping_history**, которая удаляет старые данные в журнале на основе срока их хранения.  
  
 **—** _уровень_ verboselevel  
 Определяет уровень сообщений, добавляемых в журнал доставки журналов. *Level* — одно из следующих целых чисел:  
  
|Level|Description|  
|-----------|-----------------|  
|0|Не выводить сообщения трассировки и отладки.|  
|1|Выводить сообщения обработки ошибок.|  
|2|Выводить предупреждения и сообщения обработки ошибок.|  
|**3-5**|Выводить информационные сообщения, предупреждения и сообщения обработки ошибок. Это значение по умолчанию.|  
|4|Выводить все сообщения отладки и трассировки.|  
  
 **-logintimeout** _timeout_value_  
 Указывает период времени, выделенный для попытки входа на экземпляр сервера до истечения времени ожидания. Значение по умолчанию — 15 секунд. *timeout_value* имеет **тип int**_._  
  
 **-querytimeout** _timeout_value_  
 Указывает период времени, выделенный для запуска указанной операции до истечения времени ожидания. Значение по умолчанию — без времени ожидания. *timeout_value* имеет **тип int**_._  
  
## <a name="remarks"></a>Remarks  
 Рекомендуется по возможности применять для выполнения резервирования, копирования и восстановления соответствующие задания. Их запуск производится через вызов хранимой процедуры [sp_start_job](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql) .  
  
 Журнал доставки журналов, созданный программой **sqllogship** , смешивается с журналом, создаваемым заданиями доставки журналов. При частом использовании программы **sqllogship** в конфигурациях доставки журналов стоит рассмотреть отключение заданий доставки журналов. Дополнительные сведения см. в статье [Disable or Enable a Job](../ssms/agent/disable-or-enable-a-job.md).  
  
 Приложение **sqllogship** , sqllogship. exe, устанавливается в каталог X:\PROGRAM Files\Microsoft SQL Server\120\Tools\Binn.  
  
## <a name="permissions"></a>Разрешения  
 **sqllogship** использует проверку подлинности Windows. Учетной записи Windows, от которой выполняется команда, необходимы доступ к каталогу Windows и разрешения [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Это требование зависит от того, какой параметр задается командой **sqllogship** : **-backup**, **-copy**или **-restore** .  
  
|Параметр|Доступ к каталогу|Разрешения|  
|------------|----------------------|-----------------|  
|**— Резервное копирование**|Требует доступа по чтению и записи в каталог резервной копии.|Необходимы те же разрешения, что и для инструкции BACKUP. Дополнительные сведения см. в разделе [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql).|  
|**-Copy**|Требует доступа на чтение к каталогу резервной копии и доступа на запись в каталог копии.|Требует таких же разрешений, что и хранимая процедура [sp_help_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql) .|  
|**— восстановление**|Требует доступа на чтение-запись в каталог копирования.|Требует тех же разрешений, что и инструкция RESTORE. Дополнительные сведения см. в разделе [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).|  
  
> [!NOTE]  
>  Чтобы выяснить пути к каталогам резервной копии и копии, необходимо запустить хранимую процедуру **sp_help_log_shipping_secondary_database** или просмотреть таблицу **log_shipping_secondary** в базе данных **msdb**. Пути к каталогам резервной копии и назначения находятся в столбцах **backup_source_directory** и **backup_destination_directory** соответственно.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;доставки журналов&#41;](../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [log_shipping_primary_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-primary-databases-transact-sql)   
 [log_shipping_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-secondary-transact-sql)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)   
 [sp_help_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql)   
 [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)  
  
  
