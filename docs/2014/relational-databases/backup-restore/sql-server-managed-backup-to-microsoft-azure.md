---
title: SQL Server управляемого резервного копирования в Azure | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: afa01165-39e0-4efe-ac0e-664edb8599fd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ab44323dfabd389113351e413751b7a230c176e6
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70175762"
---
# <a name="sql-server-managed--backup-to-azure"></a>SQL Server управляемого резервного копирования в Azure
  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]управляет SQL Server резервным копированием в службу хранилища BLOB-объектов Azure и автоматизирует их. Стратегия резервного копирования, используемая [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], основана на сроке хранения и рабочей нагрузке в базе данных. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] поддерживает восстановление на момент времени для указанного периода хранения.   
Службы [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] могут быть включены на уровне базы данных или на уровне экземпляра для управления всеми базами данных в экземпляре SQL Server. SQL Server может выполняться локально или в размещенных средах, таких как виртуальная машина Azure. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]рекомендуется использовать для SQL Server, выполняющихся на виртуальных машинах Azure.  
  
## <a name="benefits-of-automating-sql-server-backup-using-includess_smartbackupincludesss-smartbackup-mdmd"></a>Преимущества автоматизации резервного копирования SQL Server с помощью [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
-   В настоящий момент автоматизация резервного копирования множества баз данных требует разработки стратегии резервного копирования, написания специального кода и планирования резервного копирования. С помощью [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] можно предоставить только необходимые параметры срока хранения и места расположения. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]планирует, выполняет и поддерживает резервные копии.  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] можно настроить на уровне базы данных или с параметрами по умолчанию для экземпляра SQL Server. Автоматизация резервного копирования [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] с помощью имеет следующие преимущества.  
  
    -   Установив настройки по умолчанию на уровне экземпляра, вы можете применить их к любой базе данных, созданной впоследствии, тем самым обеспечив своевременное резервное копирование и предотвратив потерю данных.  
  
    -   Включив [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] и настроив срок хранения на уровне базы данных, вы можете переопределить настройки по умолчанию, заданные на уровне экземпляра. Так вы получаете более гранулярный контроль над возможностями восстановления определенной базы данных.  
  
-   При использовании [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] вам не нужно указывать тип или частоту резервного копирования базы данных.  Вы указываете срок хранения и [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] определяет тип и частоту резервного копирования для базы данных, которая хранит резервные копии в службе хранилища BLOB-объектов Azure. Дополнительные сведения о наборе критериев [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] , используемых для создания стратегии резервного копирования, см. в разделе [компоненты и основные понятия](#Concepts) этой статьи.  
  
-   Если конфигурация предусматривает использование шифрования, имеется дополнительная защита резервных данных. Дополнительные сведения см. в разделе [Шифрование резервных копий](backup-encryption.md) .  
  
 Дополнительные сведения о преимуществах использования хранилища BLOB-объектов Azure для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] резервного копирования см. в статье [SQL Server резервное копирование и восстановление с помощью службы хранилища BLOB-объектов Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) .  
  
## <a name="terms-and-definitions"></a>Термины и определения  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
 Функция SQL Server, которая автоматизирует резервное копирование и обслуживает резервные копии на основе срока хранения.  
  
 Срок хранения  
 По сроку хранения [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] определяет, какие файлы резервных копий следует оставить в хранилище для восстановления базы данных на момент времени в течение заданного периода.  Поддерживаемые значения находятся в диапазоне от 1 до 30 дней.  
  
 Цепочка журналов  
 Непрерывная последовательность резервных копий журналов называется цепочкой журналов. Цепочка журналов начинается с полной резервной копии базы данных.  
  
##  <a name="Concepts"></a>Требования, понятия и компоненты  
  
  
###  <a name="Security"></a> Permissions  
 Transact-SQL — это основной интерфейс, используемый для настройки и отслеживания [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Как правило, для запуска хранимых процедур конфигурации **db_backupoperator** роль базы данных с разрешениями **ALTER ANY CREDENTIAL** и `EXECUTE` разрешения на хранимую процедуру **sp_delete_backuphistory** .  Для хранимых процедур и функций, используемых для просмотра информации, обычно требуются разрешения `Execute` для хранимой процедуры и `Select` для функции соответственно.  
  
###  <a name="Prereqs"></a> Предварительные требования  
 **Предварительные условия.**  
  
 **Служба хранилища Azure** используется [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для хранения файлов резервных копий.    Основные понятия, структура и требования для создания учетной записи хранения Azure подробно описаны в разделе [Общие сведения о ключевых компонентах и концепциях](sql-server-backup-to-url.md#intorkeyconcepts) раздела **SQL Server Backup to URL** .  
  
 **Учетные данные SQL** используются для хранения сведений, необходимых для проверки подлинности в учетной записи хранения Azure. В объекте учетных данных SQL хранится имя учетной записи и данные ключа доступа. Дополнительные сведения см. в разделе [Введение в ключевые компоненты и основные понятия](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) статьи **SQL Server Backup to URL** . Пошаговое руководство по созданию учетных данных SQL для хранения данных проверки подлинности службы [хранилища Azure см. в разделе занятие 2. Создайте SQL Server учетные](../../tutorials/lesson-2-create-a-sql-server-credential.md)данные.  
  
###  <a name="Concepts_Components"></a>Основные понятия и ключевые компоненты  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] — это функция, управляющая операциями резервного копирования. Он хранит метаданные в базе данных **msdb** и использует системные задания для записи полных резервных копий базы данных и журнала транзакций.  
  
#### <a name="components"></a>Компоненты  
 Transact-SQL — это основной интерфейс для взаимодействия с [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Системные хранимые процедуры используются для активации, настройки и отслеживания [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Системные функции используются для получения существующих параметров конфигурации, значений параметров и данных файлов резервных копий. Расширенные события используются для отображения ошибок и предупреждений. Механизмы предупреждений включаются с помощью заданий агента SQL Server и управления на основе политик SQL Server. Далее представлен список объектов и описание их функций по отношению к [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 Можно также настроить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]с помощью командлетов PowerShell. SQL Server Management Studio поддерживает восстановление резервных копий, созданных [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] , с помощью задачи **Восстановление базы данных** .  
  
|||  
|-|-|  
|Системный объект|Описание|  
|**MSDB**|Хранит метаданные, журнал резервного копирования для всех резервных копий, созданных [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
|[smart_admin. Set _db_backup &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)|Системные хранимые процедуры для включения и настройки [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для базы данных.|  
|[smart_admin. Set _instance_backup &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/dn451009(v=sql.120).aspx)|Системная хранимая процедура для включения и настройки [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] параметров по умолчанию для экземпляра SQL Server.|  
|[smart_admin. sp_ backup_master_switch &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)|Системные хранимые процедуры для приостановки и возобновления [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
|[smart_admin. sp_set_parameter &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)|Системные хранимые процедуры для включения и настройки мониторинга [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Примеры: включение расширенных событий, настроек почты для уведомлений.|  
|[smart_admin. sp_backup_on_demand &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)|Системная хранимая процедура, используемая для выполнения Специального резервного копирования базы данных, которая может использоваться [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] без нарушения цепочки журналов.|  
|[smart_admin. fn_backup_db_config &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-backup-db-config-transact-sql)|Системная функция, возвращающая текущее [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] состояние и значения конфигурации для базы данных или для всех баз данных в экземпляре.|  
|[smart_admin. fn_is_master_switch_on &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-is-master-switch-on-transact-sql)|Системная функция, которая возвращает состояние основного переключателя.|  
|[smart_admin. sp_get_backup_diagnostics &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-get-backup-diagnostics-transact-sql)|Системная хранимая процедура, используемая для получения событий, зарегистрированных расширенными событиями.|  
|[smart_admin. fn_get_parameter &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)|Системная функция, возвращающая текущие значения системных параметров резервного копирования, таких как настройки мониторинга и почтовые настройки для оповещений.|  
|[smart_admin. fn_available_backups &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql)|Хранимая процедура, используемая для получения доступных резервных копий заданной базы данных или всех баз данных в экземпляре.|  
|[smart_admin. fn_get_current_xevent_settings &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)|Системная функция, которая возвращает текущие настройки расширенных событий.|  
|[smart_admin. fn_get_health_status &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-health-status-transact-sql)|Системная функция, которая возвращает объединенное число ошибок, зарегистрированных расширенными событиями для указанного периода.|  
|[Мониторинг SQL Server управляемого резервного копирования в Azure](sql-server-managed-backup-to-microsoft-azure.md)|Расширенные события для наблюдения, уведомления по электронной почте об ошибках и предупреждениях, управления на основе политик SQL Server для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
  
#### <a name="backup-strategy"></a>Стратегия резервного копирования  
 **Стратегия резервного копирования [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], используемая:**  
  
 Тип запланированных резервных копий и частоты резервного копирования определяется на основе рабочей нагрузки в базе данных. Настройки срока хранения определяют длительность хранения файлов резервных копий в хранилище и для восстановления базы данных на момент времени в течение срока хранения.  
  
 **Соглашения об именовании контейнеров и имен файлов резервных копий:**  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]называет контейнер службы хранилища Azure, используя имя экземпляра SQL Server для всех баз данных, Кроме баз данных доступности.  Для баз данных доступности идентификатор GUID группы доступности используется для именования контейнера службы хранилища Azure.  
  
 Имя файла резервной копии для баз данных, не связанных с доступностью, имеет следующий формат: Имя создается с помощью первых 40 символов имени базы данных, идентификатора GUID базы данных без "-" и отметки времени. Между сегментами в качестве разделителей вставляется подчеркивание. Для полной резервной копии используется расширение **BAK** , а для резервной копии журналов — **LOG** . Для баз данных группы доступности в дополнении к схеме именования, описанной выше, после 40 символов имени базы данных добавляется GUID группы доступности. Значение GUID базы данных группы доступности — это значение для group_database_id в sys.databases.  
  
 **Полное резервное копирование базы данных:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] агент планирует полную резервную копию базы данных, если выполняется одно из следующих условий.  
  
-   Функция [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] включается для базы данных впервые, или функция [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] активируется с параметрами по умолчанию на уровне экземпляра.  
  
-   Увеличение журнала после создания полной резервной копии не меньше 1 ГБ.  
  
-   Максимальный интервал времени (1 неделя) прошел с момента последнего полного резервного копирования.  
  
-   Цепочка журналов прервана. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] периодически проверяет, сохранилась ли цепочка журналов, сравнивая первый и последний номера LSN файлов резервной копии. Если по какой-то причине цепочка журналов прервана, [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] планирует полное резервное копирование базы данных. Самая распространенная причина разрыва цепочки журналов — выполнение команды резервного копирования с помощью Transact-SQL или задачи резервного копирования в SQL Server Management Studio.  К другим возможным причинам относится случайное удаление фалов журнала резервного копирования или случайная перезапись резервных копий.  
  
 **Резервная копия журнала транзакций:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] планирует резервное копирование журнала, если выполняется одно из следующих условий.  
  
-   Не удается обнаружить историю резервного копирования журналов. Это условие обычно выполняется, если [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] включается впервые.  
  
-   Используемый объем журнала транзакций равен 5 МБ или больше.  
  
-   Достигнут максимальный интервал времени (2 часа) с момента создания последней резервной копии журналов.  
  
-   Каждый раз, когда резервная копия журнала транзакций отстает от полной резервной копии базы данных, целью является сохранение цепочки журналов до полной резервной копии.  
  
#### <a name="retention-period-settings"></a>Параметры срока хранения  
 При включении резервного копирования необходимо задать срок хранения в днях: минимальное значение — 1 день, максимальное — 30 дней.  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] оценивает возможность восстановления базы данных на момент времени в течение заданного периода, чтобы определить, какие файлы резервной копии необходимо сохранить, а какие — удалить. Параметр backup_finish_date резервной копии используется для определения и сопоставления времени, заданного настройками срока хранения.  
  
#### <a name="important-considerations"></a>Важные соображения  
 Существуют определенные рекомендации, влияние которых на операции [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] необходимо понять. Они перечислены ниже.  
  
-   Если для базы данных выполняется текущее задание полного резервного копирования базы данных, [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ожидает завершения текущего задания до перехода к следующему заданию полного резервного копирования этой же базы данных. Аналогичным образом в заданный момент времени может выполняться только одно задание резервного копирования журнала транзакций. Однако операции полного резервного копирования базы данных и резервного копирования журнала транзакций могут выполняться одновременно. Ошибки записываются в журнал как расширенные события.  
  
-   Если запланировано больше 10 параллельных операций полного резервного копирования базы данных, через канал отладки расширенных событий передается предупреждение. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] хранит очередь приоритетов для оставшихся баз данных, для которых нужно создать резервные копии, пока все операции резервного копирования не будут запланированы и завершены.  
  
###  <a name="support_limits"></a>Ограничения поддержки  
 Далее представлены некоторые ограничения, характерные для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
-   [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]агент поддерживает резервное копирование только баз данных: Полные резервные копии и журналы.  Автоматическое резервное копирование файлов не поддерживается.  
  
-   Операции [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в текущий момент поддерживаются с помощью Transact-SQL. Мониторинг и устранение неполадок доступны с использованием расширенных событий. Поддержка PowerShell и SMO позволяет только настраивать параметры хранения и срока хранения по умолчанию для экземпляра SQL Server, а также контролировать состояние резервной копии и общую работоспособность на основе политик управления SQL Server.  
  
-   Системные базы данных не поддерживаются.  
  
-   Служба хранилища BLOB-объектов Azure — это единственный поддерживаемый вариант хранилища резервных копий. Резервные копии на диски или ленточные накопители не поддерживаются.  
  
-   В настоящее время максимальный размер файла, допустимый для страничного BLOB-объекта в службе хранилища Azure, составляет 1 ТБ. Файлы резервных копий, превышающие размер в 1 ТБ, вызовут ошибку. Во избежание этой ситуации рекомендуется для больших баз данных использовать сжатие и проверять размер файла резервной копии до настройки [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Вы можете либо проверить резервное копирование на локальный диск, либо вручную создать резервную копию в службе хранилища Azure `BACKUP TO URL` с помощью инструкции Transact-SQL. Дополнительные сведения см. в разделе [SQL Server Backup to URL](sql-server-backup-to-url.md).  
  
-   Модели восстановления: Поддерживаются только базы данных, для которых настроена модель полного или с неполным протоколированием.  Базы данных с простой моделью восстановления не поддерживаются.  
  
-   [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] может накладывать определенные ограничения, если она настроена с другими технологиями, поддерживающими резервное копирование, высокий уровень доступности и аварийное восстановление. Дополнительные сведения см [. в статье SQL Server управляемое резервное копирование в Azure: Взаимодействие и сосуществование](../../database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
|||  
|-|-|  
|**Описания задач**|**Раздел**|  
|Такие базовые задачи, как настройка [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] для базы данных или настройка параметров по умолчанию на уровне экземпляра, отключение [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] на уровне экземпляра или базы данных, приостановка и перезапуск [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[SQL Server управляемого резервного копирования в Azure — параметры хранения и хранения](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|  
|**Показано** Пошаговые инструкции по настройке и мониторингу [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Настройка управляемого резервного копирования SQL Server в Azure](enable-sql-server-managed-backup-to-microsoft-azure.md)|  
|**Показано** Пошаговые инструкции по настройке и мониторингу [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] баз данных в группе доступности.|[Настройка управляемого резервного копирования SQL Server в Azure для групп доступности](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)|  
|Средства, понятия и задачи, связанные с мониторингом [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Мониторинг SQL Server управляемого резервного копирования в Azure](sql-server-managed-backup-to-microsoft-azure.md)|  
|Средства и сведения для устранения неполадок [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|[Устранение неполадок SQL Server управляемого резервного копирования в Azure](../../database-engine/troubleshooting-sql-server-managed-backup-to-windows-azure.md)|  
  
## <a name="see-also"></a>См. также  
 [SQL Server резервного копирования и восстановления с помощью службы хранилища BLOB-объектов Azure](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
 [SQL Server резервное копирование на URL-адрес](sql-server-backup-to-url.md)   
 [SQL Server управляемого резервного копирования в Azure: Взаимодействие и сосуществование](../../database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)   
 [Устранение неполадок SQL Server управляемого резервного копирования в Azure](../../database-engine/troubleshooting-sql-server-managed-backup-to-windows-azure.md)  
  
  
