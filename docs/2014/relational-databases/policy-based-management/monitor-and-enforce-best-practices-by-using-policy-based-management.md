---
title: Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 46788407-187e-4b0b-bfe4-529af8d77c60
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e21317e2019fe1530e346567a5767a1dfc18c329
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165424"
---
# <a name="monitor-and-enforce-best-practices-by-using-policy-based-management"></a>Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик
  Управление на основе политик позволяет наблюдать за рекомендациями для [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет набор файлов политик, что можно импортировать в качестве политик рекомендаций и затем оценивать эти политики для набора целей, которая включает экземпляры, объекты экземпляров, баз данных или объекты базы данных. Политики можно оценивать вручную или устанавливать их для оценки набора целей согласно расписанию либо тому или иному событию. Дополнительные сведения об управлении на основе политик см. в статье [Администрирование серверов с помощью управления на основе политик](administer-servers-by-using-policy-based-management.md).  
  
## <a name="policy-and-rules-for-database-engine"></a>Политика и правила для компонента Database Engine  
 В следующей таблице перечислены политики, которые входят в состав установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и содержатся сведения о правилах рекомендаций, которые вычисляет Каждая политика. Политики хранятся в виде XML-файлов и должны импортироваться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об импорте политик см. в статье [Импорт политики управления на основе политик](import-a-policy-based-management-policy.md).  
  
|Имя политики|Правило рекомендации|  
|-----------------|------------------------|  
|Алгоритм шифрования асимметричных ключей|[Стойкость шифрования асимметричных ключей](asymmetric-keys-encryption-strength.md)|  
|Размещение резервной копии и файла данных|[Файлы резервной копии и файлы базы данных должны находиться на отдельных устройствах](../../database-engine/backup-files-must-be-on-separate-devices-from-the-database-files.md)|  
|Расположение файлов данных и журнала|[Размещение файлов данных и файлов журнала на различных дисках](place-data-and-log-files-on-separate-drives.md)|  
|Автоматическое закрытие базы данных|[Задание значения OFF для параметра базы данных AUTO_CLOSE](set-the-auto-close-database-option-to-off.md)|  
|Автоматическое сжатие базы данных|[Задание значения параметра базы данных AUTO_SHRINK, равного OFF](set-the-auto-shrink-database-option-to-off.md)|  
|Параметры сортировки базы данных|[Задание параметров сортировки пользовательских баз данных в соответствии с параметрами баз данных master и model](../../database-engine/set-collation-user-defined-databases-match-master-model-databases.md)|  
|Проверка страниц базы данных|[Задание значения CHECKSUM для параметра базы данных PAGE_VERIFY](set-the-page-verify-database-option-to-checksum.md)|  
|Состояние страницы базы данных|[Проверка целостности базы данных с потенциально поврежденными страницами](check-integrity-of-database-with-suspect-pages.md)|  
|Разрешения гостя|[Разрешения гостя для пользовательских баз данных](guest-permissions-on-user-databases.md)|  
|Дата последнего успешного резервного копирования|[Устаревшая резервная копия](outdated-backup.md)|  
|Роли Public не предоставлены разрешения на сервер|[Разрешения роли сервера public](server-public-permissions.md)|  
|SQL Server: перекрытие 32-разрядных Affinity Mask|[Правильный Affinity Mask и перекрытие маска схожести ввода-вывода](correct-affinity-mask-and-affinity-input-and-output-mask-overlap.md)|  
|SQL Server: перекрытие 64-разрядной маски сходства|[Правильный Affinity Mask и перекрытие маска схожести ввода-вывода](correct-affinity-mask-and-affinity-input-and-output-mask-overlap.md)|  
|SQL Server: маска сходства|[Сохранение значения маски сходства по умолчанию](keep-the-affinity-mask-default-value.md)|  
|SQL Server: пороговый интервал ожидания блокированных процессов|[Увеличение или отключение порога заблокированных процессов](increase-or-disable-blocked-process-threshold.md)|  
|SQL Server: трассировка по умолчанию|[Отключение предусмотренных по умолчанию файлов журнала трассировки](default-trace-log-files-disabled.md)|  
|SQL Server: динамические блокировки|[Сохранение предусмотренного по умолчанию значения параметра конфигурации блокировок](keep-the-locks-configuration-option-default-value.md)|  
|SQL Server: использование упрощенных пулов|[Отключение использования упрощенных пулов](disable-lightweight-pooling.md)|  
|SQL Server: режим входа|[Выбор режима проверки подлинности](../security/choose-an-authentication-mode.md)|  
|SQL Server: максимальная степень параллелизма|[Задание параметра максимальной степени параллелизма для оптимальной производительности](set-the-max-degree-of-parallelism-option-for-optimal-performance.md)|  
|SQL Server: максимальное число рабочих потоков для 32-разрядной версии SQL Server 2000|[Проверка параметра максимального числа рабочих потоков](verify-max-worker-threads-setting.md)|  
|SQL Server: максимальное число рабочих потоков для 64-разрядной версии SQL Server 2000|[Проверка параметра максимального числа рабочих потоков](verify-max-worker-threads-setting.md)|  
|SQL Server: максимальное число рабочих потоков для SQL Server 2005 и более поздних версий|[Проверка параметра максимального числа рабочих потоков](verify-max-worker-threads-setting.md)|  
|SQL Server: размер сетевого пакета|[Размер сетевого пакета не должен превышать 8060 байт](network-packet-size-should-not-exceed-8060-bytes.md)|  
|SQL Server: истечение действия пароля|[Истечение срока действия пароля имени входа SQL Server](sql-server-login-password-expiration.md)|  
|SQL Server: политика паролей|[Стойкость пароля имени входа SQL Server](sql-server-login-password-strength.md)|  
|Шифрование пользовательских баз данных симметричным ключом|[Симметричные ключи в пользовательских базах данных](symmetric-keys-on-user-databases.md)|  
|Симметричный ключ для базы данных master|[Симметричные ключи в системных базах данных](symmetric-keys-on-system-databases.md)|  
|Симметричный ключ для системных баз данных|[Симметричные ключи в системных базах данных](symmetric-keys-on-system-databases.md)|  
|Доверенная база данных|[Бит доверия](trustworthy-bit.md)|  
|Журнал событий Windows: ошибка из-за повреждения дискового ресурса кластера|[Определение неполадок хост-адаптера SCSI](detect-scsi-host-adapter-issues.md)|  
|Журнал событий Windows: ошибка управления драйвером устройства|[Ошибка управления драйвером устройства](device-driver-control-error.md)|  
|Журнал событий Windows, ошибка: устройство не готово|[Ошибка отсутствия готовности устройства](device-not-ready-error.md)|  
|Журнал событий Windows: ошибка запроса ввода-вывода|[Обнаружения запроса неудачных входов и выходов](detect-failed-input-and-output-requests.md)|  
|Журнал событий Windows: предупреждение об отложенном вводе-выводе|[Проверка на наличие проблем задержки ввода-вывода в подсистеме дискового ввода-вывода](check-disk-input-and-output-subsystem-for-io-delay-problems.md)|  
|Журнал событий Windows: ошибка ввода-вывода при сбое страницы физической памяти|[Ошибка ввода-вывода во время сбоев страниц физической памяти](input-and-output-error-during-hard-page-fault.md)|  
|Журнал событий Windows: ошибка при повторном считывании|[Проверка на наличие проблем повторного чтения в подсистеме дискового ввода-вывода](check-disk-input-output-subsystem-for-read-retry-problems.md)|  
|Журнал событий Windows: ошибка из-за истечения времени ожидания ввода-вывода системы хранения|[Время ожидания ввода-вывода для системы хранения](storage-system-input-output-time-out.md)|  
|Журнал событий Windows: сбой в системе|[Непредвиденные сбои системы](unexpected-system-failures.md)|  
  
## <a name="see-also"></a>См. также:  
 [Работа с аспектами управления на основе политик](working-with-policy-based-management-facets.md)  
  
  
