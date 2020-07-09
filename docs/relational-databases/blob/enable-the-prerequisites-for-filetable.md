---
title: Включение необходимых компонентов для таблицы FileTable | Документация Майкрософт
description: Чтобы использовать таблицы FileTable, сначала включите FILESTREAM, укажите каталог и задайте определенные параметры и уровни доступа. Узнайте, как выполнить все предварительные требования.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], prerequisites
ms.assetid: 6286468c-9dc9-4eda-9961-071d2a36ebd6
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
ms.openlocfilehash: fc5ba7ab181e07552f9865eff482d67e292c0249
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767993"
---
# <a name="enable-the-prerequisites-for-filetable"></a>Включение необходимых компонентов для таблицы FileTable
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Описывает способ включения компонентов, обязательных для создания и использования таблиц FileTable.  
  
##  <a name="enabling-the-prerequisites-for-filetable"></a><a name="EnablePrereq"></a> Включение необходимых компонентов для FileTable  
 Чтобы включить необходимые компоненты для создания и использования таблиц FileTable, включите следующие элементы:  
  
-   **На уровне экземпляра.**  
  
    -   [Включение FILESTREAM на уровне экземпляра](#BasicsFilestream)  
  
-   **На уровне базы данных.**  
  
    -   [Предоставление файловой группы FILESTREAM на уровне базы данных](#filegroup)  
  
    -   [Включение нетранзакционного доступа на уровне базы данных](#BasicsNTAccess)  
  
    -   [Указание каталога для таблиц FileTable на уровне базы данных](#BasicsDirectory)  
  
##  <a name="enabling-filestream-at-the-instance-level"></a><a name="BasicsFilestream"></a> Включение FILESTREAM на уровне экземпляра  
 Таблицы FileTable расширяют возможности функции FILESTREAM в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поэтому, прежде чем будет возможно создавать и использовать таблицы FileTable, необходимо включить функцию FILESTREAM для доступа к операциям файлового ввода-вывода на уровне Windows и в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="how-to-enable-filestream-at-the-instance-level"></a><a name="HowToFilestream"></a> Как включить функцию FILESTREAM на уровне экземпляра  
 Сведения о включении FILESTREAM см. в разделе [Включение и настройка FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md).  
  
 При вызове **sp_configure** для включения FILESTREAM на уровне экземпляра необходимо установить параметр filestream_access_level равным 2. Дополнительные сведения см. в статье [Параметр конфигурации сервера "уровень доступа файлового потока"](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).  
  
###  <a name="how-to-allow-filestream-through-the-firewall"></a><a name="firewall"></a> Как разрешить FILESTREAM через брандмауэр  
 Сведения о разрешении FILESTREAM через брандмауэр см. в разделе [Configure a Firewall for FILESTREAM Access](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md).  
  
##  <a name="providing-a-filestream-filegroup-at-the-database-level"></a><a name="filegroup"></a> Предоставление файловой группы FILESTREAM на уровне базы данных  
 Для создания в базе данных таблиц FileTables эта база должна иметь файловую группу FILESTREAM. Дополнительные сведения об этом предварительном требовании см. в статье [Создание базы данных FILESTREAM-Enabled](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
##  <a name="enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsNTAccess"></a> Включение нетранзакционного доступа на уровне базы данных  
 Таблицы FileTable позволяют приложениям Windows получать дескрипторы файлов Windows для данных FILESTREAM без необходимости транзакции. Чтобы разрешить такой нетранзакционный доступ к файлам, хранящимся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо указать нужный уровень нетранзакционного доступа на уровне базы данных, в которой будут содержаться таблицы FileTable.  
  
###  <a name="how-to-check-whether-non-transactional-access-is-enabled-on-databases"></a><a name="HowToCheckAccess"></a> Как проверить состояние нетранзакционного доступа (включен или выключен)  
 Выполнить запрос к представлению каталога [sys.database_filestream_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md) и проверить столбцы **non_transacted_access** и **non_transacted_access_desc**.  

```sql
SELECT DB_NAME(database_id), non_transacted_access, non_transacted_access_desc  
    FROM sys.database_filestream_options;  
GO  
```

###  <a name="how-to-enable-non-transactional-access-at-the-database-level"></a><a name="HowToNTAccess"></a> Как включить нетранзакционный доступ на уровне базы данных  
 Доступными уровнями нетранзакционного доступа являются FULL, READ_ONLY и OFF.  
  
 **Указание уровня нетранзакционного доступа с помощью Transact-SQL**  
 - При **create a new database** вызовите инструкцию [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md) с параметром **NON_TRANSACTED_ACCESS** FILESTREAM.

   ```sql
   CREATE DATABASE database_name  
     WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
   ```

- При **изменении существующей базы данных** вызовите инструкцию [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md) с параметром **NON_TRANSACTED_ACCESS** FILESTREAM.

   ```sql
   ALTER DATABASE database_name  
     SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
   ```

 **Задание уровня нетранзакционного доступа в среде SQL Server Management Studio**  
 Можно задать уровень нетранзакционного доступа в поле **Нетранзакционный доступ к файловому потоку** на странице **Параметры** диалогового окна **Свойства базы данных** . Дополнительные сведения об этом диалоговом окне см. в статье [Свойства базы данных (страница "Параметры")](../../relational-databases/databases/database-properties-options-page.md).  
  
##  <a name="specifying-a-directory-for-filetables-at-the-database-level"></a><a name="BasicsDirectory"></a> Указание каталога для таблиц FileTable на уровне базы данных  
 При включении нетранзакционного доступа к файлам на уровне базы данных можно при необходимости в то же время указать имя каталога с помощью параметра **DIRECTORY_NAME** . Если при включении нетранзакционного доступа не указано имя каталога, то необходимо ввести его позже, прежде чем будет возможно создать таблицу FileTable в базе данных.  
  
 В иерархии папок FileTable этот каталог на уровне базы данных является дочерним по отношению к общему ресурсу для FILESTREAM на уровне экземпляра и родительским по отношению к таблицам FileTable, созданным в базе данных. Дополнительные сведения см. в статье [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
###  <a name="how-to-specify-a-directory-for-filetables-at-the-database-level"></a><a name="HowToDirectory"></a> Как указать каталог для таблиц FileTable на уровне базы данных  
 Указанное имя должно быть уникальным в экземпляре для каталогов уровня базы данных.  
  
**Указание каталога для таблиц FileTable с помощью языка Transact-SQL**  
- При **create a new database** вызовите инструкцию [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md) с параметром **DIRECTORY_NAME** FILESTREAM.

   ```sql
   CREATE DATABASE database_name  
     WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
   GO  
   ```

-   При **изменении существующей базы данных** вызовите инструкцию [ALTER DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md) с параметром **DIRECTORY_NAME** FILESTREAM. Если эти параметры используются для изменения имени каталога, то база данных должна быть заблокирована в монопольном режиме при отсутствии открытых дескрипторов файлов.  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   При **подключении базы данных** вызовите инструкцию [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md) с параметром **FOR ATTACH** и **DIRECTORY_NAME** FILESTREAM.  
  
    ```sql  
    CREATE DATABASE database_name  
        FOR ATTACH WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   При **восстановлении базы данных** вызовите инструкцию [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md) с параметром **DIRECTORY_NAME** FILESTREAM.  
  
    ```sql  
    RESTORE DATABASE database_name  
        WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
 **Задание каталога для таблиц FileTable в среде SQL Server Management Studio**  
 Можно указать имя каталога в поле **Имя каталога FILESTREAM** на странице **Параметры** диалогового окна **Свойства базы данных** . Дополнительные сведения об этом диалоговом окне см. в статье [Свойства базы данных (страница "Параметры")](../../relational-databases/databases/database-properties-options-page.md).  
  
###  <a name="how-to-view-existing-directory-names-for-the-instance"></a><a name="viewnames"></a> Как просмотреть существующие имена каталогов для экземпляра  
 Чтобы просмотреть список существующих имен каталогов для экземпляра, выполните запрос к представлению каталога [sys.database_filestream_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md) и проверьте столбец **filestream_database_directory_name**.  
  
```sql  
SELECT DB_NAME ( database_id ), directory_name  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="requirements-and-restrictions-for-the-database-level-directory"></a><a name="ReqDirectory"></a> Требования и ограничения для уровня базы данных каталога  
  
-   При вызове метода **CREATE DATABASE** или **ALTER DATABASE** параметр **DIRECTORY_NAME**является необязательным. Если значение **DIRECTORY_NAME**не указано, имя каталога имеет значение NULL. Тем не менее невозможно создать таблицу FileTable в базе данных, пока не указано значение для параметра **DIRECTORY_NAME** на уровне базы данных.  
  
-   Указываемое имя каталога должно соответствовать требованиям файловой системы для допустимых имен каталогов.  
  
-   Если база данных содержит таблицы FileTable, нельзя вернуть параметр **DIRECTORY_NAME** в значение NULL.  
  
-   Операция присоединения или восстановления базы данных завершится ошибкой, если новая база данных имеет такое же значение параметра **DIRECTORY_NAME** , так как уже существует в целевом экземпляре. Укажите уникальное значение для параметра **DIRECTORY_NAME** при вызове инструкции **CREATE DATABASE FOR ATTACH** или **RESTORE DATABASE**.  
  
-   При обновлении существующей базы данных до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]значение **DIRECTORY_NAME** равно NULL.  
  
-   При включении или отключении нетранзакционного доступа на уровне базы данных операция не проверяет, было ли указано имя каталога и является ли оно уникальным.  
  
-   При удалении базы данных, в которой включены таблицы FileTable, каталог на уровне базы данных и все структуры каталогов всех находящихся в ней таблиц FileTable удаляются.  
  
  
