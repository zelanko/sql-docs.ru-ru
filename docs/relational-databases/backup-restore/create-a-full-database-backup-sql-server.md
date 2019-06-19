---
title: Создание полной резервной копии базы данных (SQL Server) | Документация Майкрософт
ms.custom: sqlfreshmay19
ms.date: 05/29/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c90a3cf1f74eb588bd6faa657a3f47d7e57df453
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66403057"
---
# <a name="create-a-full-database-backup-sql-server"></a>Создание полной резервной копии базы данных (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом разделе описывается создание полной резервной копии базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или PowerShell.  
  

Сведения о резервном копировании SQL Server в службу хранилища BLOB-объектов Azure см. в разделах [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) и [Резервное копирование SQL Server по URL-адресу](../../relational-databases/backup-restore/sql-server-backup-to-url.md).  
  
##  <a name="Restrictions"></a> Ограничения  
  
-   Инструкция BACKUP не разрешена в явных и неявных транзакциях.    
-   Резервные копии, созданные более поздними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не могут быть восстановлены в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].   
-   Основные и дополнительные сведения о понятиях и задачах, связанных с резервным копированием см. в [этой статье](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
## <a name="Recommendations"></a> Рекомендации  
  
-   По мере увеличения размера базы данных полное резервное копирование занимает больше времени и требует больше дискового пространства. Для больших баз данных может потребоваться, кроме полных резервных копий, создавать также и [разностные резервные копии баз данных](../../relational-databases/backup-restore/differential-backups-sql-server.md). Дополнительные сведения см. в разделе [SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md).    
-   Размер полной резервной копии базы данных вы можете вычислить с помощью системной хранимой процедуры [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) .    
-   По умолчанию каждая успешная операция резервного копирования добавляет запись в журнал ошибок служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и в журнал системных событий. Если резервное копирование выполняется часто, сообщения об успешном завершении операций накапливаются быстро, что приводит к стремительному увеличению журналов ошибок! Это может осложнить поиск других сообщений. Если работа существующих скриптов не зависит от записей журнала резервного копирования, то их можно отключить с помощью флага трассировки 3226. Дополнительные сведения см. в разделе [Флаги трассировки (Transact-SQL)](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).  
  
##  <a name="Security"></a> безопасность  
 Для резервной копии базы данных свойству TRUSTWORTHY присваивается значение OFF. Дополнительные сведения о том, как задать для параметра TRUSTWORTHY значение ON, см. в разделе [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , параметры **PASSWORD** и **MEDIAPASSWORD** не поддерживаются при создании резервных копий. Все еще вы можете восстанавливать резервные копии, созданные с паролями.  
  
##  <a name="Permissions"></a> Permissions  
 Разрешения BACKUP DATABASE и BACKUP LOG назначены по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенным ролям базы данных **db_owner** и **db_backupoperator** .  
  
 Проблемы, связанные с владельцем и разрешениями у физических файлов на устройстве резервного копирования, могут помешать операции резервного копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность считывать и записывать данные на устройстве; учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , **должна** иметь разрешения на запись. Однако процедура [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md), добавляющая запись для устройства резервного копирования в системные таблицы, не проверяет разрешения на доступ к файлу. Проблемы физического файла устройства резервного копирования могут не проявляться до момента доступа к физическому ресурсу во время операции резервного копирования или восстановления.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
>  При создании задания резервного копирования с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]вы можете сформировать соответствующий скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](../../t-sql/statements/backup-transact-sql.md) , нажав кнопку **Скрипт** и выбрав назначение скрипта.  
  
### <a name="back-up-a-database"></a>Резервное копирование базы данных  
  
1.  После подключения к соответствующему экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **в обозревателе объектов**разверните дерево сервера, щелкнув его имя.    
1.  Разверните узел **Базы данных**и выберите пользовательскую базу данных или разверните узел **Системные базы данных** и выберите системную базу данных.    
1.  Щелкните правой кнопкой мыши базу данных, выберите пункт **Задачи**, а затем команду **Создать резервную копию**. Откроется диалоговое окно **Резервное копирование базы данных** .  
1. Выберите из раскрывающегося списка **базу данных** для восстановления. 
1. В раскрывающемся списке **Тип резервной копии** выберите **Полный**. 
1. В разделе **Компонент резервного копирования** выберите **База данных**. 
1. В разделе **Назначения** воспользуйтесь раскрывающимся списком **Создать резервную копию на** для выбора назначения резервного копирования. Нажмите кнопку **Добавить**, чтобы добавить дополнительные назначения и/или объекты резервного копирования. Чтобы удалить носитель резервной копии, выберите его и нажмите кнопку **Удалить**. Чтобы просмотреть содержимое существующего назначения резервного копирования, выберите его и щелкните **Содержимое**.
1. (Необязательно) Просмотрите другие доступные параметры на страницах **Параметры носителя** и **Параметры резервного копирования**. Дополнительные сведения о различных параметрах резервного копирования см. на [странице "Общие"](back-up-database-general-page.md), [странице "Параметры носителя"](back-up-database-media-options-page.md) и [странице "Параметры резервного копирования"](back-up-database-backup-options-page.md). 



### <a name="additional-information"></a>Дополнительные сведения
- При создании полной резервной копии базы данных можно создавать разностные резервные копии; дополнительные сведения см. в разделе [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).  
- Также можно установить флажок **Архивная копия только для копирования** , чтобы создать резервную копию только для копирования. *Резервная копия только для копирования* — это резервная копия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая не зависит от обычной последовательности создания традиционных резервных копий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Резервные копии только для копирования (SQL Server)](../../relational-databases/backup-restore/copy-only-backups-sql-server.md).  Резервная копия только для копирования недоступна для типа резервной копии **Разностная**.  
- Параметр **Перезаписать носитель** может быть недоступен на странице **Параметры носителя** при резервном копировании на URL-адрес. 


## <a name="ssms-examples"></a>Примеры для SSMS  

Для следующих примеров создайте тестовую базу данных со следующим кодом Transact-SQL:

```sql
USE [master]
GO

CREATE DATABASE [SQLTestDB]
GO

USE [SQLTestDB]
GO
CREATE TABLE SQLTest (
    ID INT NOT NULL PRIMARY KEY,
    c1 VARCHAR(100) NOT NULL,
    dt1 DATETIME NOT NULL DEFAULT getdate()
)
GO


USE [SQLTestDB]
GO

INSERT INTO SQLTest (ID, c1) VALUES (1, 'test1')
INSERT INTO SQLTest (ID, c1) VALUES (2, 'test2')
INSERT INTO SQLTest (ID, c1) VALUES (3, 'test3')
INSERT INTO SQLTest (ID, c1) VALUES (4, 'test4')
INSERT INTO SQLTest (ID, c1) VALUES (5, 'test5')
GO

SELECT * FROM SQLTest
GO
```

### <a name="a-full-back-up-to-disk-to-default-location"></a>A. Полное резервное копирование на диск в расположение по умолчанию
В этом примере база данных `SQLTestDB` будет заархивирована на диск в папку резервных копий по умолчанию.  Резервное копирование `SQLTestDB` никогда не выполнялось.
1.  В **обозревателе объектов**подключитесь к экземпляру компонента SQL Server Database Engine и разверните его.
2.  Разверните узел **Базы данных**, щелкните правой кнопкой `SQLTestDB`, укажите на пункт **Задачи**и выберите **Создать резервную копию...**
3.  Нажмите кнопку **ОК**.

![Создание резервной копии SQL](media/quickstart-backup-restore-database/backup-db-ssms.png) 
 

### <a name="b--full-back-up-to-disk-to-non-default-location"></a>**Б.  Полное резервное копирование на диск в нестандартное расположение**
В этом примере база данных `SQLTestDB` будет заархивирована на диск в папку `F:\MSSQL\BAK`.  Ранее резервные копии `SQLTestDB` уже создавались.
1.  В **обозревателе объектов**подключитесь к экземпляру компонента SQL Server Database Engine и разверните его.
2.  Разверните узел **Базы данных**, щелкните правой кнопкой `Sales`, укажите на пункт **Задачи**и выберите **Создать резервную копию...**
3.  На странице **Общие** в разделе **Назначение** выберите **Диск** в раскрывающемся списке **Создать резервную копию на:** .
4.  Щелкайте элемент **Удалить**, пока не будут удалены все существующие файлы резервных копий.
5.  Нажмите кнопку **Добавить**, чтобы открыть диалоговое окно **Выбор места расположения резервной копии**.
6.  Введите `F:\MSSQL\BAK\Sales_20160801.bak` в текстовом поле **имя файла** .
7.  Нажмите кнопку **ОК**.
8.  Нажмите кнопку **ОК**.

![Изменить расположение базы данных](media/create-a-full-database-backup-sql-server/change-db-location.png)

### <a name="c--create-an-encrypted-backup"></a>**В.  Создание зашифрованной резервной копии**
В этом примере база данных `SQLTestDB` будет заархивирована с шифрованием в папку резервных копий по умолчанию.  

1.  В **обозревателе объектов**подключитесь к экземпляру компонента SQL Server Database Engine и разверните его.
1. Откройте окно **Новый запрос** и выполните следующие команды, чтобы создать [**главный ключ базы данных**](../../relational-databases/security/encryption/create-a-database-master-key.md) и [**сертификат**](../../t-sql/statements/create-certificate-transact-sql.md) в вашей базе данных `SQLTestDB`. 

    ```sql
    USE [SQLTestDB]
        
    -- Create the database master key
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
    
    
    -- Create the certificate
    CREATE CERTIFICATE MyCertificate   
    ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
    EXPIRY_DATE = '20201031';  
    GO  
    ```

1.  В **обозревателе объектов** разверните узел **Базы данных**, щелкните правой кнопкой `SQLTestDB`, укажите на пункт **Задачи** и выберите **Создать резервную копию...** .
1.  На странице **Параметры носителя** в разделе **Перезапись носителя** выберите **Создать резервную копию в новом наборе носителей и удалить все существующие резервные наборы данных**.
1.  На странице **Параметры резервного копирования** в разделе **Шифрование** установите флажок **Зашифровать резервную копию** .
1.  В раскрывающемся списке "Алгоритм" выберите **AES 256**.
1.  В раскрывающемся списке **Сертификат или асимметричный ключ** выберите `MyCertificate`.
1.  Нажмите кнопку **ОК**.

![Зашифрованная резервная копия](media/create-a-full-database-backup-sql-server/encrypted-backup.png)

### <a name="d--back-up-to-the-azure-blob-storage-service"></a>**Г.  Резервное копирование в службу хранилища BLOB-объектов Azure**


В следующих трех примера выполняется полное резервное копирование базы данных `Sales` в службу хранилища больших двоичных объектов Microsoft Azure.  Имя учетной записи хранилища — `mystorageaccount`.  Контейнер называется `myfirstcontainer`.  Для краткости первые четыре шага перечислены здесь однократно, а все примеры начинаются с **шага 5**.

1.  В **обозревателе объектов**подключитесь к экземпляру компонента SQL Server Database Engine и разверните его.
2.  Разверните узел **Базы данных**, щелкните правой кнопкой `Sales`, укажите на пункт **Задачи**и выберите **Создать резервную копию...**
3.  На странице **Общие** в разделе **Назначение** выберите **URL-адрес** в раскрывающемся списке **Создать резервную копию на:** .
4.  Нажмите кнопку **Добавить** , чтобы открыть диалоговое окно **Выбор места расположения резервной копии** .

#### <a name="striped-backup-to-url-and-a-sql-server-credential-already-exists"></a>Чередующееся резервное копирование с использованием уже существующих URL-адреса и учетных данных SQL Server

Хранимая политика доступа была создана с правами на чтение, запись и составление списков.  Учетные данные SQL Server, `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`, были созданы с использованием подписанного URL-адреса, который связан с хранимой политикой доступа.  

   5.   Выберите `https://mystorageaccount.blob.core.windows.net/myfirstcontainer` из текстового поля **Контейнер хранилища Azure:**
   6.  В текстовом поле **Файл резервной копии:** введите `Sales_stripe1of2_20160601.bak`.
   7.  Нажмите кнопку **ОК**.
   8.  Повторите шаги **4** и **5**.
   9.  В текстовом поле **Файл резервной копии:** введите `Sales_stripe2of2_20160601.bak`.
   10.  Нажмите кнопку **ОК**.
   11.   Нажмите кнопку **ОК**.

#### <a name="a-shared-access-signature-exists-and-a-sql-server-credential-does-not-exist"></a>Подписанный URL-адрес существует, а учетные данные SQL Server — нет.

  5.    Введите `https://mystorageaccount.blob.core.windows.net/myfirstcontainer` в текстовом поле **Контейнер хранилища Azure:**  
  6.    Введите подписанный URL-адрес в текстовом поле **Политика подписанных URL-адресов:** .  
  7.    Нажмите кнопку **ОК**.  
  8.    Нажмите кнопку **ОК**.


#### <a name="a-shared-access-signature-does-not-exist"></a>Подписанный URL-адрес не существует.

  5.    Щелкните **Создать контейнер**, чтобы открыть диалоговое окно **Соединение с подпиской Microsoft**.   
  6.    Выполните все действия в диалоговом окне **Соединение с подпиской Microsoft** и нажмите кнопку **ОК** , чтобы вернуться в диалоговое окно **Выбор места назначения резервной копии** .  См. дополнительные сведения в разделе [Соединение с подпиской Microsoft Azure](../../relational-databases/backup-restore/connect-to-a-microsoft-azure-subscription.md) .  
  7.    Нажмите кнопку **ОК** в диалоговом окне **Выбор места назначения резервной копии** .  
  8.    Нажмите кнопку **ОК**.

  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
### <a name="create-a-full-database-backup"></a>Создание полной резервной копии базы данных  
  
1.  Выполните инструкцию BACKUP DATABASE для создания полной резервной копии базы данных, указав следующее:  
  
    -   имя базы данных для создания резервной копии;   
    -   устройство резервного копирования, на которое записывается полная резервная копия базы данных.    
     Базовая структура синтаксиса [!INCLUDE[tsql](../../includes/tsql-md.md)] для полного резервного копирования базы данных:  
  
     BACKUP DATABASE *database*  
       TO *backup_device* [ **,** ...*n* ]    
     [ WITH *with_options* [ **,** ...*o* ] ] ;  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |*database*|База данных для резервного копирования.|  
    |*backup_device* [ **,** ...*n* ]|Указывает список от 1 до 64 устройств резервного копирования, используемых для создания резервной копии. Можно указать как физическое устройство резервного копирования, так и соответствующее логическое устройство, если оно уже определено. Для указания физического устройства резервного копирования используйте параметр DISK или TAPE.<br /><br /> { DISK &#124; TAPE } **=** _physical\_backup\_device\_name_<br /><br /> Дополнительные сведения см. в разделе [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md).|  
    |WITH *with_options* [ **,** ...*o* ]|При необходимости можно указать один или несколько дополнительных параметров, *o*. Сведения о некоторых основных параметрах см. в пункте 2.|  
  
2.  При необходимости укажите один или несколько параметров WITH. Здесь описываются некоторые основные параметры WITH. Сведения обо всех параметрах WITH см. в разделе [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md).  

Основные параметры WITH резервного набора данных:

- **{ COMPRESSION | NO_COMPRESSION }** : Только в версии [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] и выше указано, выполняется ли команда [backup compression](../../relational-databases/backup-restore/backup-compression-sql-server.md) для этой резервной копии, переопределяя значение по умолчанию на уровне сервера. 
- **ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)** : Только для SQL Server 2014 и выше укажите используемый алгоритм шифрования, а также сертификат или асимметричный ключ для шифрования.
- **DESCRIPTION** **=** { **'** _текст_ **'**  |  **@** _текстовая\_переменная_ }: Задает произвольное текстовое описание резервного набора данных. В этой строке может содержаться до 255 символов.  
- **NAME = { *имя_резервного_набора_данных* |  **@** _переменная\_резервного\_набора\_данных_ }** : Указывает имя резервного набора данных. Длина имени не может превышать 128 символов. Если параметр NAME не указан, то имя является пустым. 
  
 
По умолчанию команда BACKUP добавляет резервную копию в существующий набор носителей, сохраняя существующие резервные наборы данных. Чтобы явно указать это, используйте параметр NOINIT. Сведения о присоединении к существующим резервным наборам данных см. в разделе [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md).  

Чтобы отформатировать носитель резервной копии используется параметр FORMAT:  

FORMAT [ **,** MEDIANAME **=** { *media_name* |  **@** _media\_name\_variable_ } ] [ **,** MEDIADESCRIPTION **=** { *text* |  **@** _text\_variable_ } ]  
Используйте предложение FORMAT при первом использовании носителя или при необходимости перезаписать существующие данные. При необходимости назначьте новому носителю имя и описание.  

> [!IMPORTANT]  
>  Будьте предельно осторожны, используя предложение FORMAT инструкции BACKUP, так как оно удаляет все резервные копии, сохраненные ранее на носителе резервных копий.  
  
##  <a name="TsqlExample"></a> Примеры Transact-SQL  
Для следующих примеров создайте тестовую базу данных со следующим кодом Transact-SQL:

```sql
USE [master]
GO

CREATE DATABASE [SQLTestDB]
GO

USE [SQLTestDB]
GO
CREATE TABLE SQLTest (
    ID INT NOT NULL PRIMARY KEY,
    c1 VARCHAR(100) NOT NULL,
    dt1 DATETIME NOT NULL DEFAULT getdate()
)
GO


USE [SQLTestDB]
GO

INSERT INTO SQLTest (ID, c1) VALUES (1, 'test1')
INSERT INTO SQLTest (ID, c1) VALUES (2, 'test2')
INSERT INTO SQLTest (ID, c1) VALUES (3, 'test3')
INSERT INTO SQLTest (ID, c1) VALUES (4, 'test4')
INSERT INTO SQLTest (ID, c1) VALUES (5, 'test5')
GO

SELECT * FROM SQLTest
GO
```
  
#### <a name="a-back-up-to-a-disk-device"></a>**А. Резервное копирование на дисковое устройство**  
 В следующем примере производится резервное копирование всей базы данных `SQLTestDB` на диск и создание нового набора носителей с помощью параметра `FORMAT` .  
  
```sql  
USE SQLTestDB;  
GO  
BACKUP DATABASE SQLTestDB  
TO DISK = 'Z:\SQLServerBackups\SQLTestDB.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of SQLTestDB';  
GO  
```  
  
#### <a name="b-back-up-to-a-tape-device"></a>**Б. Резервное копирование на ленточное устройство**  
 В следующем примере создается полная резервная копия базы данных `SQLTestDB` на ленте в дополнение к предыдущим резервными копиям.  
  
```sql  
USE SQLTestDB;  
GO  
BACKUP DATABASE SQLTestDB  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of SQLTestDB';  
GO  
```  
  
#### <a name="c-back-up-to-a-logical-tape-device"></a>**В. Резервное копирование на логическое ленточное устройство**  
 В следующем примере создается логическое устройство резервного копирования для ленточного накопителя. Затем показано, как производится полное резервное копирование базы данных SQLTestDB на этот накопитель.  
  
```sql  
-- Create a logical backup device,   
-- SQLTestDB_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'SQLTestDB_Bak_Tape', '\\.\tape0'; USE SQLTestDB;  
GO  
BACKUP DATABASE SQLTestDB  
   TO SQLTestDB_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'SQLTestDB_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of SQLTestDB';  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
Используйте командлет **Backup-SqlDatabase** . Чтобы явно указать, что это полная резервная копия базы данных, задайте параметр **-BackupAction**  со значением по умолчанию **Database**. Данный параметр является необязательным для полных резервных копий баз данных.  

## <a name="powershell-examples"></a>Примеры для PowerShell

### <a name="a--full-local-backup"></a>A.  Полная локальная резервная копия 
В следующем примере создается полная резервная копия базы данных `MyDB` в заданном по умолчанию расположении резервного копирования на экземпляре сервера `Computer\Instance`. Дополнительно в этом примере указывается параметр **-BackupAction Database**.  
```powershell 
Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
```
 
### <a name="b--full-backup-to-microsoft-azure"></a>Б.  Полная резервная копия в Microsoft Azure 
В следующем примере создается полная резервная копия базы данных `Sales` в экземпляре `MyServer` службы хранилища больших двоичных объектов Microsoft Azure.  Хранимая политика доступа была создана с правами на чтение, запись и составление списков.  Учетные данные SQL Server, `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`, были созданы с использованием подписанного URL-адреса, который связан с хранимой политикой доступа.  Команда PowerShell использует параметр **BackupFile** для указания расположения (URL-адреса) и имени файла резервной копии.

```powershell  
import-module sqlps;
$container = 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer';
$FileName = 'Sales.bak';
$database = 'Sales';
$BackupFile = $container + '/' + $FileName ;
  
Backup-SqlDatabase -ServerInstance "MyServer" -Database $database -BackupFile $BackupFile;
```
 
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Резервное копирование базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
-   [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)
-   [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)
-   [Восстановление резервной копии базы данных в простой модели восстановления (Transact-SQL)](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)
-   [Восстановление базы данных до точки сбоя в модели полного восстановления (Transact-SQL)](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)
-   [Восстановление базы данных в новом расположении (SQL Server)](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)
-   [Использование мастера планов обслуживания](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a>См. также раздел  
- [Устранение неполадок операций резервного копирования и восстановления SQL Server](https://support.microsoft.com/kb/224071)
- [Общие сведения о резервном копировании (SQL Server)](../../relational-databases/backup-restore/backup-overview-sql-server.md)
- [Резервные копии журналов транзакций (SQL Server)](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)
- [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)
- [sp_addumpdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)
- [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
- [Резервное копирование базы данных (страница "Общие")](../../relational-databases/backup-restore/back-up-database-general-page.md)
- [Резервное копирование базы данных (страница "Параметры резервного копирования")](../../relational-databases/backup-restore/back-up-database-backup-options-page.md)
- [Разностные резервные копии (SQL Server)](../../relational-databases/backup-restore/differential-backups-sql-server.md)
- [Полные резервные копии баз данных (SQL Server)](../../relational-databases/backup-restore/full-database-backups-sql-server.md)  
  
  
