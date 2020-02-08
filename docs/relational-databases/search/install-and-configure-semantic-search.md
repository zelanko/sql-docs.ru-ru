---
title: Установка и настройка семантического поиска | Документация Майкрософт
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], installing
- semantic search [SQL Server], configuring
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: cac6ecd59b270feecea3590c33c9dc8c41f1edcc
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73638030"
---
# <a name="install-and-configure-semantic-search"></a>Установка и настройка семантического поиска
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Описывает компоненты, необходимые для статистического семантического поиска, и способы их установки и проверки.  
  
## <a name="install-semantic-search"></a>установить семантический поиск  
  
###  <a name="HowToCheckInstalled"></a> Проверка установки семантического поиска  
 Отправьте запрос к свойству **IsFullTextInstalled** функции метаданных [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md).  
  
 Возвращаемое значение 1 указывает, что установлен компонент Full-Text Search и семантический поиск. Возвращаемое значение 0 указывает, что они не установлены.  
  
```sql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="BasicsSemanticSearch"></a> Установка семантического поиска  
 Чтобы установить семантический поиск, выберите пункт **Полнотекстовый и семантический поиск** на странице **Устанавливаемые средства** во время установки SQL Server.  
  
 Статистический семантический поиск зависит от полнотекстового поиска. Эти два дополнительных компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливаются совместно.  
  
## <a name="install-the-semantic-language-statistics-database"></a>Установка базы данных семантической статистики языка  
 Средства семантического поиска имеют дополнительную внешнюю зависимость; речь идет о базе данных семантической статистики языка. Эта база данных содержит статистические языковые модели, необходимые для семантического поиска. Каждая база данных статистики семантики языка содержит языковые модели для всех языков, поддерживаемых семантическим индексированием.  
  
###  <a name="HowToCheckDatabase"></a> Проверка установки базы данных семантической статистики языка  
 Отправьте запрос в представление каталога [sys.fulltext_semantic_language_statistics_database (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
 Если для экземпляра установлена и зарегистрирована база данных семантической статистики языка, то результаты запроса содержат единственную строку сведений о базе данных.  
  
```sql  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="HowToInstallModel"></a> Установка, присоединение и регистрация базы данных семантической статистики языка  
 База данных семантической статистики языка не устанавливается программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы установить базу данных семантической статистики языка как обязательный компонент для семантического индексирования, выполните следующие действия.  
  
 **1. Установите базу данных семантической статистики языка.**  
 
 1.  Найдите базу данных семантической статистики языка на установочном носителе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или загрузите её из Интернета.  
  
        1.  Найдите пакет установщика Windows с именем файла **SemanticLanguageDatabase.msi** на установочном носителе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
        2.  Скачайте пакет установщика со страницы [Семантическая статистика языка Microsoft® SQL Server® 2016](https://www.microsoft.com/download/details.aspx?id=52681) в центре загрузки [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
2.  Запустите пакет установщика Windows **SemanticLanguageDatabase.msi** , чтобы извлечь базу данных и файл журнала.  
  
     Предусмотрена возможность изменить каталог назначения (не обязательно). По умолчанию установщик извлекает файлы в папку **Microsoft Semantic Language Database** внутри каталога Program Files. Файл MSI содержит файл базы данных и файл журнала в сжатом виде.  
  
3.  Переместите извлеченный файл базы данных и файл журнала в подходящее расположение в файловой системе.  
  
     Если оставить эти файлы на месте, невозможно будет извлечь еще одну копию базы данных для другого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!IMPORTANT]  
    >  Файлу базы данных и файлу журнала при извлечении базы данных семантической статистики языка назначаются ограниченные разрешения в расположении по умолчанию в файловой системе. В результате, если вы перейдете из расположения по умолчанию, у вас может не оказаться разрешения на присоединение базы данных. Если при попытке присоединить базу данных возникает ошибка, переместите файлы или проверьте и исправьте разрешения файловой системы соответствующим образом.  
  
 **2. Присоедините базу данных семантической статистики языка.**
   
 Присоедините базу данных к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] или вызвав инструкцию [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md) с синтаксисом **FOR ATTACH**. Дополнительные сведения см. в разделе [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
 По умолчанию база данных имеет имя **semanticsdb**. При присоединении можно присвоить базе данных другое имя (необязательно). Это имя необходимо предоставить при регистрации базы данных в следующем шаге.  
  
```sql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 В этих образцах кода предполагается, что вы переместили базу данных из расположения по умолчанию в новое место хранения.  
  
 **3. Зарегистрируйте базу данных семантической статистики языка.** 
  
 Вызовите хранимую процедуру [sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql.md) и укажите имя, присвоенное базе данных при присоединении.  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  

##  <a name="reqinstall"></a> Требования и ограничения по установке и удалению базы данных семантической статистики языка  
  
-   Вы можете присоединить и зарегистрировать только одну базу данных статистики семантики языка для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Для каждого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на одном компьютере требуется отдельная физическая копия базы данных семантической статистики языка. Присоедините по одной копии к каждому экземпляру.  
  
-   Нельзя отсоединить действительную базу данных статистики семантики языка и заменить ее произвольной базой данных с тем же именем. Это приведет к сбоям активного или последующего заполнения индекса.  
  
-   База данных статистики семантики языка доступна только для чтения. Вы не можете настраивать эту базу данных. Если содержимое этой базы данных будет изменено каким-то образом, то результаты будущего семантического индексирования станут недетерминированными. Чтобы восстановить исходное состояние данных, можно удалить измененную базу данных, загрузить и прикрепить новую неизмененную копию базы данных.  
  
-   Имеется возможность отключить или удалить базу данных статистики семантики языка. Если имеются какие-либо активные операции индексирования, которым принадлежат блокировки для чтения, установленные для базы данных, то операция удаления или отсоединения окончится неудачей или завершится в связи с истечением времени ожидания. Это согласуется с существующим поведением. Операции семантического индексирования после удаления базы данных будут оканчиваться неудачей.  
 
##  <a name="HowToUnregister"></a> Удаление базы данных семантической статистики языка  

###  <a name="unregister-detach-and-remove-the-semantic-language-statistics-database"></a>Отмена регистрации, отсоединение и удаление базы данных семантической статистики языка 

 **1. Отмените регистрацию базы данных семантической статистики языка.**
   
 Вызовите хранимую процедуру [sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql.md). Необходимость предоставлять имя базы данных отсутствует, поскольку экземпляр может иметь только одну базу данных семантической статистики языка.  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 **2. Отсоедините базу данных семантической статистики языка.**  
 
 Вызовите хранимую процедуру [sp_detach_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) и укажите имя базы данных.  
  
```sql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 **3. Удалите базу данных семантической статистики языка.**  
 
 После отмены регистрации и отсоединения базы данных можно просто удалить файл базы данных. Программы удаления не существует, отсутствует пункт в списке **Программы и компоненты** на панели управления.  
  
## <a name="install-optional-support-for-newer-document-types"></a>Установка дополнительной поддержки для новых типов документов  
  
###  <a name="office"></a> Установка последних фильтров для Microsoft Office и других типов документов Майкрософт  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает самые последние средства разбиения по словам и парадигматические модули [!INCLUDE[msCoName](../../includes/msconame-md.md)] , но не устанавливает последние фильтры для документов [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office и других типов документов [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Эти фильтры необходимы для индексирования документов, созданных в последних версиях программ [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office и других приложениях [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Чтобы загрузить последние фильтры, см. раздел [Пакеты фильтров Microsoft Office 2010](https://www.microsoft.com/download/details.aspx?id=17062). (На данный момент не существует пакета фильтров для Office 2013 или Office 2016).
  
  
