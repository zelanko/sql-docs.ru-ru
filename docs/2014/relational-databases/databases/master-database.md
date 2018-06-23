---
title: База данных master | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- master database [SQL Server], about
- master database [SQL Server]
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
caps.latest.revision: 46
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 88cbd58a75ff8b7ceaaf93843bb685cdcb8dc11b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188490"
---
# <a name="master-database"></a>База данных master
  База данных **master** содержит всю системную информацию о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . в том числе общие для всего экземпляра метаданные, такие как сведения об учетных записях входа, конечных точках и связанных серверах, а также параметры конфигурации системы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]системные объекты больше не хранятся в базе данных **master** ; они хранятся в [базе данных ресурсов](resource-database.md). Кроме этого, в базе данных **master** регистрируются все остальные базы данных и хранится информация о расположении их файлов. Здесь же [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]хранит сведения об инициализации. Таким образом, если база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] master **недоступна, запустить** невозможно.  
  
## <a name="physical-properties-of-master"></a>Физические свойства базы данных master  
 Исходные конфигурационные значения файлов данных и журнала базы данных **master** приведены в следующей таблице. Размеры этих файлов могут немного изменяться в зависимости от выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Файл|Логическое имя|Физическое имя|Увеличение размера файлов|  
|----------|------------------|-------------------|-----------------|  
|Первичные данные|master|master.mdf|Автоувеличение на 10 % до заполнения диска.|  
|Журнал|mastlog|mastlog.ldf|Автоувеличение на 10 % до максимального размера в 2 ТБ.|  
  
 Сведения о перемещении файлов данных и журнала базы данных **master** см. в разделе [Перемещение системных баз данных](system-databases.md).  
  
### <a name="database-options"></a>Параметры базы данных  
 Значения по умолчанию всех параметров базы данных **master** и сведения о том, можно ли их изменять, приведены в следующей таблице. Чтобы просмотреть текущие настройки этих параметров, используйте представление каталога [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) .  
  
|Параметр базы данных|Значение по умолчанию|Можно ли изменить|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|ON|Нет|  
|ANSI_NULL_DEFAULT|OFF|Да|  
|ANSI_NULLS|OFF|Да|  
|ANSI_PADDING|OFF|Да|  
|ANSI_WARNINGS|OFF|Да|  
|ARITHABORT|OFF|Да|  
|AUTO_CLOSE|OFF|Нет|  
|AUTO_CREATE_STATISTICS|ON|Да|  
|AUTO_SHRINK|OFF|Нет|  
|AUTO_UPDATE_STATISTICS|ON|Да|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Да|  
|CHANGE_TRACKING|OFF|Нет|  
|CONCAT_NULL_YIELDS_NULL|OFF|Да|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Да|  
|CURSOR_DEFAULT|GLOBAL|Да|  
|Параметры доступности базы данных|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|Нет<br /><br /> Нет<br /><br /> Нет|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Да|  
|DB_CHAINING|ON|Нет|  
|ENCRYPTION|OFF|Нет|  
|NUMERIC_ROUNDABORT|OFF|Да|  
|PAGE_VERIFY|CHECKSUM|Да|  
|PARAMETERIZATION|SIMPLE|Да|  
|QUOTED_IDENTIFIER|OFF|Да|  
|READ_COMMITTED_SNAPSHOT|OFF|Нет|  
|RECOVERY|SIMPLE|Да|  
|RECURSIVE_TRIGGERS|OFF|Да|  
|Параметры компонента Service Broker|DISABLE_BROKER|Нет|  
|TRUSTWORTHY|OFF|Да|  
  
 Описание этих параметров баз данных см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="restrictions"></a>Ограничения  
 База данных **master** не поддерживает следующие операции:  
  
-   добавление файлов или файловых групп;  
  
-   Изменение параметров сортировки. Параметрами сортировки по умолчанию являются параметры сортировки сервера.  
  
-   Изменение владельца базы данных. Владельцем**master** является **sa**.  
  
-   создание полнотекстового каталога или полнотекстового индекса;  
  
-   создание триггеров для системных таблиц базы данных;  
  
-   Удаление базы данных.  
  
-   Удаление пользователя **guest** из базы данных.  
  
-   Включение системы отслеживания измененных данных.  
  
-   Участие в зеркальном отображении базы данных.  
  
-   Удаление первичной файловой группы, первичного файла данных или файла журнала.  
  
-   Переименование базы данных или первичной файловой группы.  
  
-   Перевод базы данных в режим «вне сети» (OFFLINE).  
  
-   Перевод базы данных или первичной файловой группы в режим READ_ONLY.  
  
## <a name="recommendations"></a>Рекомендации  
 При работе с базой данных **master** учитывайте следующие рекомендации:  
  
-   всегда имейте в наличии актуальную резервную копию базы данных **master** ;  
  
-   после выполнения следующих операций как можно быстрее создавайте резервную копию базы данных **master** :  
  
    -   создание, изменение или удаление базы данных;  
  
    -   изменение значений параметров конфигурации сервера или базы данных;  
  
    -   изменение или удаление учетных записей входа;  
  
-   не создавайте в базе данных **master**пользовательские объекты. Если сделать это, придется чаще создавать резервные копии базы данных **master** .  
  
-   не устанавливайте в базе данных **master** параметр TRUSTWORTHY в значение ON.  
  
## <a name="what-to-do-if-master-becomes-unusable"></a>Что делать, если база данных master становится непригодна к использованию  
 Если база данных **master** непригодна к использованию, ее можно вернуть в нормальное состояние следующими способами.  
  
-   Восстановить базу данных **master** на основе актуальной резервной копии.  
  
     Если экземпляр сервера удалось запустить, базу данных **master** можно восстановить из полной резервной копии. Дополнительные сведения см. в разделе [Восстановление базы данных master (Transact-SQL)](../backup-restore/restore-the-master-database-transact-sql.md).  
  
-   Перестроить базу данных **master** с нуля.  
  
     Если серьезное повреждение базы данных **master** не позволяет запустить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], базу данных **master**нужно перестроить. Дополнительные сведения см. в разделе [Перестроение системных баз данных](rebuild-system-databases.md).  
  
    > [!IMPORTANT]  
    >  При перестроении базы данных **master** все системные базы данных также перестраиваются.  
  
## <a name="related-content"></a>См. также  
 [Перестроение системных баз данных](rebuild-system-databases.md)  
  
 [Системные базы данных](system-databases.md)  
  
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [Перемещение файлов базы данных](move-database-files.md)  
  
  
