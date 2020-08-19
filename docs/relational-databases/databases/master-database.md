---
description: База данных master
title: База данных master | Документация Майкрософт
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], about
- master database [SQL Server]
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7be82eb5eaa61307cd5421033adc1634de9a946b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411370"
---
# <a name="master-database"></a>База данных master

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  База данных **master** содержит всю системную информацию о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . в том числе общие для всего экземпляра метаданные, такие как сведения об учетных записях входа, конечных точках и связанных серверах, а также параметры конфигурации системы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]системные объекты больше не хранятся в базе данных **master** ; они хранятся в [базе данных ресурсов](../../relational-databases/databases/resource-database.md). Кроме этого, в базе данных **master** регистрируются все остальные базы данных и хранится информация о расположении их файлов. Здесь же [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]хранит сведения об инициализации. Таким образом, если база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] master **недоступна, запустить** невозможно.  

> [!IMPORTANT]
> Для отдельных баз данных и эластичных пулов Базы данных SQL Azure используются только базы данных master и tempdb. Дополнительные сведения см. в разделе [Что являет собою сервер Базы данных SQL Azure?](https://docs.microsoft.com/azure/sql-database/sql-database-servers#what-is-an-azure-sql-database-server). Описание базы данных tempdb в контексте Базы данных SQL Azure см. в разделе [База данных tempdb в базе данных SQL](tempdb-database.md#tempdb-database-in-sql-database). Для Управляемого экземпляра SQL Azure применяются все системные базы данных. См. дополнительные сведения об [Управляемом экземпляре Базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
  
## <a name="physical-properties-of-master"></a>Физические свойства базы данных master

Исходные конфигурационные значения файлов данных и файлов журнала базы данных **master** для SQL Server и Управляемого экземпляра SQL Azure приведены в следующей таблице. Размеры этих файлов могут немного изменяться в зависимости от выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Файл|Логическое имя|Физическое имя|Увеличение размера файлов|  
|----------|------------------|-------------------|-----------------|  
|Первичные данные|master|master.mdf|Автоувеличение на 10 % до заполнения диска.|  
|Журнал|mastlog|mastlog.ldf|Автоувеличение на 10 % до максимального размера в 2 ТБ.|  
  
Сведения о перемещении файлов данных и журнала базы данных **master** см. в разделе [Перемещение системных баз данных](../../relational-databases/databases/move-system-databases.md).  

> [!IMPORTANT]
> При работе с сервером Базы данных SQL Azure пользователь не может управлять размером базы данных **master**.
  
### <a name="database-options"></a>Параметры базы данных

Значения по умолчанию для всех параметров базы данных **master** для SQL Server и Управляемого экземпляра SQL Azure и сведения о том, можно ли их изменять, приведены в следующей таблице. Чтобы просмотреть текущие настройки этих параметров, используйте представление каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) .  
  
> [!IMPORTANT]
> При работе с отдельными базами данных и эластичными пулами Базы данных SQL Azure пользователь не может управлять этими параметрами базы данных.

|Параметр базы данных|Значение по умолчанию|Можно ли изменить|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|ON|нет|  
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
|Параметры доступности базы данных|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|нет<br /><br /> нет<br /><br /> Нет|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Да|  
|DB_CHAINING|ON|нет|  
|ENCRYPTION|OFF|нет|  
|MIXED_PAGE_ALLOCATION|ON|нет|  
|NUMERIC_ROUNDABORT|OFF|Да|  
|PAGE_VERIFY|CHECKSUM|Да|  
|PARAMETERIZATION|ПРОСТОЙ|Да|  
|QUOTED_IDENTIFIER|OFF|Да|  
|READ_COMMITTED_SNAPSHOT|OFF|нет|  
|RECOVERY|ПРОСТОЙ|Да|  
|RECURSIVE_TRIGGERS|OFF|Да|  
|Параметры компонента Service Broker|DISABLE_BROKER|нет|  
|TRUSTWORTHY|OFF|Да|  
  
Описание этих параметров баз данных см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="restrictions"></a>Ограничения  
База данных **master** не поддерживает следующие операции:  
  
- добавление файлов или файловых групп;  
- Резервное копирование, для базы данных master может быть выполнено только полное резервное копирование.
- Изменение параметров сортировки. Параметрами сортировки по умолчанию являются параметры сортировки сервера.  
- Изменение владельца базы данных. Владельцем**master** является **sa**.  
- создание полнотекстового каталога или полнотекстового индекса;  
- создание триггеров для системных таблиц базы данных;  
- Удаление базы данных.  
- Удаление пользователя **guest** из базы данных.  
- Включение системы отслеживания измененных данных.  
- Участие в зеркальном отображении базы данных.  
- Удаление первичной файловой группы, первичного файла данных или файла журнала.  
- Переименование базы данных или первичной файловой группы.  
- Перевод базы данных в режим «вне сети» (OFFLINE).  
- Перевод базы данных или первичной файловой группы в режим READ_ONLY.  
  
## <a name="recommendations"></a>Рекомендации  
При работе с базой данных **master** учитывайте следующие рекомендации:  
  
- всегда имейте в наличии актуальную резервную копию базы данных **master** ;  
- после выполнения следующих операций как можно быстрее создавайте резервную копию базы данных **master** :  
  
  - создание, изменение или удаление базы данных;  
  - изменение значений параметров конфигурации сервера или базы данных;  
  - изменение или удаление учетных записей входа;  
  
- не создавайте в базе данных **master**пользовательские объекты. Если сделать это, придется чаще создавать резервные копии базы данных **master** .  
- не устанавливайте в базе данных **master** параметр TRUSTWORTHY в значение ON.  
  
## <a name="what-to-do-if-master-becomes-unusable"></a>Что делать, если база данных master становится непригодна к использованию  
 Если база данных **master** непригодна к использованию, ее можно вернуть в нормальное состояние следующими способами.  
  
- Восстановить базу данных **master** на основе актуальной резервной копии.  
  
  Если экземпляр сервера удалось запустить, базу данных **master** можно восстановить из полной резервной копии. Дополнительные сведения см. в разделе [Восстановление базы данных master (Transact-SQL)](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md).  
  
- Перестроить базу данных **master** с нуля.  
  
  Если серьезное повреждение базы данных **master** не позволяет запустить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], базу данных **master**нужно перестроить. Дополнительные сведения см. в разделе [Перестроение системных баз данных](../../relational-databases/databases/rebuild-system-databases.md).  
  
  > [!IMPORTANT]  
  >  При перестроении базы данных **master** все системные базы данных также перестраиваются.  
  
## <a name="related-content"></a>См. также  
- [Перестроение системных баз данных](../../relational-databases/databases/rebuild-system-databases.md)  
- [Системные базы данных](../../relational-databases/databases/system-databases.md)  
- [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
- [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
- [Перемещение файлов базы данных](../../relational-databases/databases/move-database-files.md)  
