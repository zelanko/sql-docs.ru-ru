---
title: База данных tempdb | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0b1265d3ef58f6ef0946937b15411b0cb79a3c20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62916894"
---
# <a name="tempdb-database"></a>База данных tempdb
  Системная база данных **tempdb** — это глобальный ресурс, доступный всем пользователям, подключенным к данному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в котором хранятся следующие объекты:  
  
-   временные объекты, созданные явно, такие как глобальные или локальные временные таблицы, временные хранимые процедуры, табличные переменные и курсоры;  
  
-   внутренние объекты, создаваемые [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], например рабочие таблицы, хранящие промежуточные результаты буферов или сортировки;  
  
-   версии строк, сформированные транзакциями изменения данных в базе данных, в которой используются транзакции изоляции моментальных снимков с зафиксированным чтением и транзакции изоляции моментальных снимков;  
  
-   версии строк, создаваемые транзакциями изменения данных для таких функций, как операции с индексами в сети, функции режима MARS и триггеры AFTER.  
  
 Операции в базе данных **tempdb** регистрируются минимально. Это позволяет откатить транзакцию. **база данных tempdb** создается повторно при каждом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запуске, чтобы система всегда начиналась с чистой копией. Временные таблицы и хранимые процедуры удаляются автоматически при отключении, и при выключении системы нет активных соединений. Таким образом, в **базе данных tempdb** нельзя сохранять данные из одного сеанса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в другой. Операции резервного копирования и восстановления не разрешены в **базе данных tempdb**.  
  
## <a name="physical-properties-of-tempdb"></a>Физические свойства базы данных tempdb  
 Следующая таблица описывает исходную конфигурацию данных и файлов журналов базы данных **tempdb** . Размеры этих файлов могут немного изменяться в зависимости от выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Файл|Логическое имя|Физическое имя|Увеличение размера файлов|  
|----------|------------------|-------------------|-----------------|  
|Первичные данные|tempdev|tempdb.mdf|Автоувеличение на 10 % до заполнения диска.|  
|Журнал|templog|templog.ldf|Автоувеличение на 10 % до максимального размера в 2 ТБ.|  
  
 Размер **базы данных tempdb** может повлиять на производительность системы. Например, если размер базы данных **tempdb** слишком мал, системная обработка может оказаться слишком занятой с автоувеличением базы данных для поддержки требования к рабочей нагрузке при каждом запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эту нагрузку можно избежать, увеличив размер **базы данных tempdb**.  
  
## <a name="performance-improvements-in-tempdb"></a>Увеличение производительности базы данных tempdb  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]производительность базы данных **tempdb** увеличена следующими способами.  
  
-   Временные таблицы и табличные переменные могут кэшироваться. Кэширование позволяет операциям по удалению и созданию временных объектов выполняться очень быстро и снижает число состязаний из-за выделения страниц.  
  
-   Усовершенствован протокол кратковременных блокировок выделения страниц. При этом снижается количество используемых кратковременных блокировок UP (обновление).  
  
-   Снижены затраты на ведение журнала базы данных **tempdb** . При этом снижается потребление пропускной способности подсистемы ввода-вывода файлом журнала базы данных **tempdb** .  
  
-   Улучшен алгоритм выделения смешанных страниц в **базе данных tempdb** .  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>Перемещение данных и файлов журналов базы данных tempdb  
 Сведения о перемещении файлов данных и журналов **tempdb** см. в разделе [Перемещение системных баз данных](system-databases.md).  
  
### <a name="database-options"></a>Параметры базы данных  
 В следующей таблице приводятся значения по умолчанию для каждого параметра базы данных **tempdb** и указывается, можно ли изменить параметр. Чтобы просмотреть текущие настройки этих параметров, используйте представление каталога [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Параметр базы данных|Значение по умолчанию|Можно ли изменить|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Да|  
|ANSI_NULL_DEFAULT|OFF|Да|  
|ANSI_NULLS|OFF|Да|  
|ANSI_PADDING|OFF|Да|  
|ANSI_WARNINGS|OFF|Да|  
|ARITHABORT|OFF|Да|  
|AUTO_CLOSE|OFF|нет|  
|AUTO_CREATE_STATISTICS|ON|Да|  
|AUTO_SHRINK|OFF|нет|  
|AUTO_UPDATE_STATISTICS|ON|Да|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Да|  
|CHANGE_TRACKING|OFF|нет|  
|CONCAT_NULL_YIELDS_NULL|OFF|Да|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Да|  
|CURSOR_DEFAULT|GLOBAL|Да|  
|Параметры доступности базы данных|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|нет<br /><br /> нет<br /><br /> нет|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Да|  
|DB_CHAINING|ON|нет|  
|ENCRYPTION|OFF|нет|  
|NUMERIC_ROUNDABORT|OFF|Да|  
|PAGE_VERIFY|Значение CHECKSUM для новых установок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Значение NONE для обновлений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Да|  
|PARAMETERIZATION|ПРОСТОЙ|Да|  
|QUOTED_IDENTIFIER|OFF|Да|  
|READ_COMMITTED_SNAPSHOT|OFF|нет|  
|RECOVERY|ПРОСТОЙ|нет|  
|RECURSIVE_TRIGGERS|OFF|Да|  
|Параметры компонента Service Broker|ENABLE_BROKER|Да|  
|TRUSTWORTHY|OFF|нет|  
  
 Описание этих баз данных см. в статье [Параметры ALTER DATABASE SET (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
## <a name="restrictions"></a>Ограничения  
 Невозможно выполнить следующие операции с базой данных **tempdb** :  
  
-   Добавление файловых групп.  
  
-   Резервное копирование и восстановление из копии.  
  
-   Изменение параметров сортировки. Параметрами сортировки по умолчанию являются параметры сортировки сервера.  
  
-   Изменение владельца базы данных. **база данных tempdb** принадлежит **SA**.  
  
-   Создание моментального снимка базы данных.  
  
-   Удаление базы данных.  
  
-   Удаление пользователя **guest** из базы данных.  
  
-   Включение системы отслеживания измененных данных.  
  
-   Участие в зеркальном отображении базы данных.  
  
-   Удаление первичной файловой группы, первичного файла данных или файла журнала.  
  
-   Переименование базы данных или первичной файловой группы.  
  
-   Выполнение инструкции DBCC CHECKALLOC.  
  
-   Выполнение инструкции DBCC CHECKCATALOG.  
  
-   Перевод базы данных в режим «вне сети» (OFFLINE).  
  
-   Перевод базы данных или первичной файловой группы в режим READ_ONLY.  
  
## <a name="permissions"></a>Разрешения  
 Любой пользователь может создавать временные объекты в базе данных tempdb. Если не предоставлены какие-либо дополнительные разрешения, то пользователи могут производить доступ только к тем объектам, которыми они владеют. Существует возможность отменить разрешение на соединение с базой данных tempdb, чтобы пользователь не мог ей пользоваться, но этого делать не рекомендуется, так как база данных tempdb необходима для работы некоторым подпрограммам.  
  
## <a name="related-content"></a>См. также  
 [Параметр SORT_IN_TEMPDB для индексов](../indexes/indexes.md)  
  
 [Системные базы данных](system-databases.md)  
  
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys. master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Перемещение файлов базы данных](move-database-files.md)  
  
## <a name="see-also"></a>См. также:  
 [Работа с базой данных tempdb в SQL Server 2005](https://chresandro.wordpress.com/2014/09/29/working-with-tempdb-in-sql-server-2005/)  
  
  
