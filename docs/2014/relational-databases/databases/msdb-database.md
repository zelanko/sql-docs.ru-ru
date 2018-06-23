---
title: База данных msdb | Документация Майкрософт
ms.custom: ''
ms.date: 11/10/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, msdb database
- alerts [SQL Server], msdb database
- jobs [SQL Server], msdb database
- msdb database [SQL Server]
ms.assetid: 5032cb2d-65a0-40dd-b569-4dcecdd58ceb
caps.latest.revision: 43
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 27c7555a412fd536db632504ce6bcc82122fa8e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192901"
---
# <a name="msdb-database"></a>База данных msdb
  База данных **msdb** используется агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для создания расписания предупреждений и заданий, а также другими компонентами, такими как среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и компоненты [!INCLUDE[ssSB](../../includes/sssb-md.md)] и Database Mail.  
  
 Например, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически поддерживает полный журнал резервного копирования и восстановления "в сети" в таблицах в базе данных **msdb**. В эти сведения включено имя стороны, выполнившей резервное копирование, время резервного копирования и устройства или файлы, в которых храниться резервная копия. Среда[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] использует эти сведения для создания плана восстановления базы данных и применения существующих резервных копий журнала транзакций. События резервного копирования для всех баз данных записываются, даже если они создаются средствами пользовательских приложений или сторонних разработчиков. Например, если приложение [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] при выполнении операций резервного копирования обращается к объектам SMO, то событие заносится в системные таблицы базы данных **msdb** , в журнал приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы защитить сведения, хранящиеся в базе данных **msdb**, рекомендуется разместить журнал транзакций **msdb** в отказоустойчивом хранилище.  
  
 По умолчанию, для базы данных **msdb** используется простая модель восстановления. Если используются таблицы [журнала резервного копирования и восстановления](../backup-restore/backup-history-and-header-information-sql-server.md) , рекомендуется использовать для базы данных **msdb**модель полного восстановления. Дополнительные сведения см. в разделе [Модели восстановления (SQL Server)](../backup-restore/recovery-models-sql-server.md). Обратите внимание, что при установке или обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а также при каждом перестроении системных баз данных с помощью программы Setup.exe для базы данных **msdb** автоматически устанавливается модель простого восстановления.  
  
> [!IMPORTANT]  
>  После любых операций, обновляющих базу данных **msdb**, например резервного копирования или восстановления любой другой базы данных, рекомендуется создать резервную копию базы данных **msdb**. Дополнительные сведения см. в разделе [Резервное копирование и восстановление системных баз данных (SQL Server)](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="physical-properties-of-msdb"></a>Физические свойства базы данных msdb  
 В следующей таблице представлен список значений начальной конфигурации данных и файлов журнала **msdb** . Размеры этих файлов могут немного изменяться в зависимости от выпуска [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
|Файл|Логическое имя|Физическое имя|Увеличение размера файлов|  
|----------|------------------|-------------------|-----------------|  
|Первичные данные|MSDBData|MSDBData.mdf|Автоувеличение на 10 % до заполнения диска.|  
|Журнал|MSDBLog|MSDBLog.ldf|Автоувеличение на 10 % до максимального размера в 2 ТБ.|  
  
 Сведения о перемещении файлов базы данных и журналов **msdb** см. в разделе [Перемещение системных баз данных](move-system-databases.md).  
  
### <a name="database-options"></a>Параметры базы данных  
 В следующей таблице приводится список значений по умолчанию для каждого параметра базы данных в **msdb** , а также возможность его изменения. Чтобы просмотреть текущие настройки этих параметров, используйте представление каталога [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Параметр базы данных|Значение по умолчанию|Можно ли изменить|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|ON|Нет|  
|ANSI_NULL_DEFAULT|OFF|Да|  
|ANSI_NULLS|OFF|Да|  
|ANSI_PADDING|OFF|Да|  
|ANSI_WARNINGS|OFF|Да|  
|ARITHABORT|OFF|Да|  
|AUTO_CLOSE|OFF|Да|  
|AUTO_CREATE_STATISTICS|ON|Да|  
|AUTO_SHRINK|OFF|Да|  
|AUTO_UPDATE_STATISTICS|ON|Да|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Да|  
|CHANGE_TRACKING|OFF|Нет|  
|CONCAT_NULL_YIELDS_NULL|OFF|Да|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Да|  
|CURSOR_DEFAULT|GLOBAL|Да|  
|Параметры доступности базы данных|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Нет<br /><br /> Да<br /><br /> Да|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Да|  
|DB_CHAINING|ON|Да|  
|ENCRYPTION|OFF|Нет|  
|NUMERIC_ROUNDABORT|OFF|Да|  
|PAGE_VERIFY|CHECKSUM|Да|  
|PARAMETERIZATION|SIMPLE|Да|  
|QUOTED_IDENTIFIER|OFF|Да|  
|READ_COMMITTED_SNAPSHOT|OFF|Нет|  
|RECOVERY|SIMPLE|Да|  
|RECURSIVE_TRIGGERS|OFF|Да|  
|Параметры компонента Service Broker|ENABLE_BROKER|Да|  
|TRUSTWORTHY|ON|Да|  
  
 Описание этих параметров баз данных см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="restrictions"></a>Ограничения  
 С базой данных **msdb** нельзя выполнить следующие действия.  
  
-   Изменение параметров сортировки. Параметрами сортировки по умолчанию являются параметры сортировки сервера.  
  
-   Удаление базы данных.  
  
-   Удаление пользователя **guest** из базы данных.  
  
-   Включение системы отслеживания измененных данных.  
  
-   Участие в зеркальном отображении базы данных.  
  
-   Удаление первичной файловой группы, первичного файла данных или файла журнала.  
  
-   Переименование базы данных или первичной файловой группы.  
  
-   Перевод базы данных в режим «вне сети» (OFFLINE).  
  
-   Перевод первичной файловой группы в режим READ_ONLY.  
  
## <a name="related-content"></a>См. также  
 [Системные базы данных](system-databases.md)  
  
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Перемещение файлов базы данных](move-database-files.md)  
  
 [Компонент Database Mail](../database-mail/database-mail.md)  
  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
