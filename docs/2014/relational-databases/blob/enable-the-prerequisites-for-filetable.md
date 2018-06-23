---
title: Включение необходимых компонентов для таблицы FileTable | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FileTables [SQL Server], prerequisites
ms.assetid: 6286468c-9dc9-4eda-9961-071d2a36ebd6
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 55279e8fd0f69fa93131f47ccf7ceb106ae2c689
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101099"
---
# <a name="enable-the-prerequisites-for-filetable"></a>Включение необходимых компонентов для таблицы FileTable
  Описывает способ включения компонентов, обязательных для создания и использования таблиц FileTable.  
  
##  <a name="EnablePrereq"></a> Включение необходимых компонентов для FileTable  
 Чтобы включить необходимые компоненты для создания и использования таблиц FileTable, включите следующие элементы:  
  
-   **На уровне экземпляра.**  
  
    -   [Включение FILESTREAM на уровне экземпляра](#BasicsFilestream)  
  
-   **На уровне базы данных.**  
  
    -   [Предоставление файловой группы FILESTREAM на уровне базы данных](#filegroup)  
  
    -   [Включение нетранзакционного доступа на уровне базы данных](#BasicsNTAccess)  
  
    -   [Указание каталога для таблиц FileTable на уровне базы данных](#BasicsDirectory)  
  
##  <a name="BasicsFilestream"></a> Включение FILESTREAM на уровне экземпляра  
 Таблицы FileTable расширяют возможности функции FILESTREAM в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поэтому, прежде чем будет возможно создавать и использовать таблицы FileTable, необходимо включить функцию FILESTREAM для доступа к операциям файлового ввода-вывода на уровне Windows и в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="HowToFilestream"></a> Инструкции. Включение функции FILESTREAM на уровне экземпляра  
 Сведения о включении FILESTREAM см. в разделе [Включение и настройка FILESTREAM](enable-and-configure-filestream.md).  
  
 При вызове `sp_configure` для включения FILESTREAM на уровне экземпляра, необходимо установить параметр filestream_access_level равным 2. Дополнительные сведения см. в статье [Параметр конфигурации сервера "уровень доступа файлового потока"](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).  
  
###  <a name="firewall"></a> Инструкции. Разрешение FILESTREAM через брандмауэр  
 Сведения о разрешении FILESTREAM через брандмауэр см. в разделе [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md).  
  
##  <a name="filegroup"></a> Предоставление файловой группы FILESTREAM на уровне базы данных  
 Для создания в базе данных таблиц FileTables эта база должна иметь файловую группу FILESTREAM. Дополнительные сведения об этом предварительном требовании см. в статье [Создание базы данных FILESTREAM-Enabled](create-a-filestream-enabled-database.md).  
  
##  <a name="BasicsNTAccess"></a> Включение нетранзакционного доступа на уровне базы данных  
 Таблицы FileTable позволяют приложениям Windows получать дескрипторы файлов Windows для данных FILESTREAM без необходимости транзакции. Чтобы разрешить такой нетранзакционный доступ к файлам, хранящимся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо указать нужный уровень нетранзакционного доступа на уровне базы данных, в которой будут содержаться таблицы FileTable.  
  
###  <a name="HowToCheckAccess"></a> Инструкции. Проверка состояния нетранзакционного доступа (включен или выключен)  
 Выполнить запрос к представлению каталога [sys.database_filestream_options (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) и проверить столбцы **non_transacted_access** и **non_transacted_access_desc**.  
  
```tsql  
SELECT DB_NAME(database_id), non_transacted_access, non_transacted_access_desc  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="HowToNTAccess"></a> Инструкции. Включение нетранзакционного доступа на уровне базы данных  
 Доступными уровнями нетранзакционного доступа являются FULL, READ_ONLY и OFF.  
  
 **Указание уровня нетранзакционного доступа с помощью Transact-SQL**  
 -   При **create a new database** вызовите инструкцию [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) с параметром **NON_TRANSACTED_ACCESS** FILESTREAM.  
  
    ```tsql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
-   При **изменении существующей базы данных** вызовите инструкцию [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) с параметром **NON_TRANSACTED_ACCESS** FILESTREAM.  
  
    ```tsql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
 **Задание уровня нетранзакционного доступа в среде SQL Server Management Studio**  
 Можно задать уровень нетранзакционного доступа в поле **Нетранзакционный доступ к файловому потоку** на странице **Параметры** диалогового окна **Свойства базы данных** . Дополнительные сведения об этом диалоговом окне см. в статье [Свойства базы данных (страница "Параметры")](../databases/database-properties-options-page.md).  
  
##  <a name="BasicsDirectory"></a> Указание каталога для таблиц FileTable на уровне базы данных  
 При включении нетранзакционного доступа к файлам на уровне базы данных можно при необходимости в то же время указать имя каталога с помощью параметра **DIRECTORY_NAME** . Если при включении нетранзакционного доступа не указано имя каталога, то необходимо ввести его позже, прежде чем будет возможно создать таблицу FileTable в базе данных.  
  
 В иерархии папок FileTable этот каталог на уровне базы данных является дочерним по отношению к общему ресурсу для FILESTREAM на уровне экземпляра и родительским по отношению к таблицам FileTable, созданным в базе данных. Дополнительные сведения см. в статье [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md).  
  
###  <a name="HowToDirectory"></a> Инструкции. Указание каталога для таблиц FileTable на уровне базы данных  
 Указанное имя должно быть уникальным в экземпляре для каталогов уровня базы данных.  
  
 **Указание каталога для таблиц FileTable с помощью языка Transact-SQL**  
 -   При **create a new database** вызовите инструкцию [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) с параметром **DIRECTORY_NAME** FILESTREAM.  
  
    ```tsql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   При **изменении существующей базы данных** вызовите инструкцию [ALTER DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) с параметром **DIRECTORY_NAME** FILESTREAM. Если эти параметры используются для изменения имени каталога, то база данных должна быть заблокирована в монопольном режиме при отсутствии открытых дескрипторов файлов.  
  
    ```tsql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   При **подключении базы данных** вызовите инструкцию [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) с параметром **FOR ATTACH** и **DIRECTORY_NAME** FILESTREAM.  
  
    ```tsql  
    CREATE DATABASE database_name  
        FOR ATTACH WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   При **восстановлении базы данных** вызовите инструкцию [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql) с параметром **DIRECTORY_NAME** FILESTREAM.  
  
    ```tsql  
    RESTORE DATABASE database_name  
        WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
 **Задание каталога для таблиц FileTable в среде SQL Server Management Studio**  
 Можно указать имя каталога в поле **Имя каталога FILESTREAM** на странице **Параметры** диалогового окна **Свойства базы данных** . Дополнительные сведения об этом диалоговом окне см. в статье [Свойства базы данных (страница "Параметры")](../databases/database-properties-options-page.md).  
  
###  <a name="viewnames"></a> Инструкции. Просмотр существующих имен каталогов для экземпляра  
 Чтобы просмотреть список существующих имен каталогов для экземпляра, выполните запрос к представлению каталога [sys.database_filestream_options (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) и проверьте столбец **filestream_database_directory_name**.  
  
```tsql  
SELECT DB_NAME ( database_id ), directory_name  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="ReqDirectory"></a> Требования и ограничения для уровня базы данных каталога  
  
-   При вызове метода **CREATE DATABASE** или **ALTER DATABASE** параметр **DIRECTORY_NAME**является необязательным. Если значение **DIRECTORY_NAME**не указано, имя каталога имеет значение NULL. Тем не менее невозможно создать таблицу FileTable в базе данных, пока не указано значение для параметра **DIRECTORY_NAME** на уровне базы данных.  
  
-   Указываемое имя каталога должно соответствовать требованиям файловой системы для допустимых имен каталогов.  
  
-   Если база данных содержит таблицы FileTable, нельзя вернуть параметр **DIRECTORY_NAME** в значение NULL.  
  
-   Операция присоединения или восстановления базы данных завершится ошибкой, если новая база данных имеет такое же значение параметра **DIRECTORY_NAME** , так как уже существует в целевом экземпляре. Укажите уникальное значение для параметра **DIRECTORY_NAME** при вызове инструкции **CREATE DATABASE FOR ATTACH** или **RESTORE DATABASE**.  
  
-   При обновлении существующей базы данных до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]значение **DIRECTORY_NAME** равно NULL.  
  
-   При включении или отключении нетранзакционного доступа на уровне базы данных операция не проверяет, было ли указано имя каталога и является ли оно уникальным.  
  
-   При удалении базы данных, в которой включены таблицы FileTable, каталог на уровне базы данных и все структуры каталогов всех находящихся в ней таблиц FileTable удаляются.  
  
  
