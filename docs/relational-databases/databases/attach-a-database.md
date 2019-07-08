---
title: Присоединение базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c7b7588801419f57d04996d6bd2cad335a9eede
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583232"
---
# <a name="attach-a-database"></a>Присоединение базы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом разделе описывается присоединение базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эту функцию можно использовать для копирования, перемещения или обновления базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="Prerequisites"></a> Предварительные требования  
  
-   Базу данных сначала необходимо отсоединить. Попытка присоединить базу данных, которая не была отсоединена, приведет к возникновению ошибки. Дополнительные сведения см. в разделе [Отсоединение базы данных](../../relational-databases/databases/detach-a-database.md).  
  
-   При присоединении базы данных должны быть доступны все файлы данных (файлы MDF и LDF). Если у какого-либо файла данных путь отличается от того, каким он был при первом создании или последнем присоединении, необходимо указать текущий путь к файлу.  
  
-   Если при присоединении базы данных файлы MDF и LDF находятся в разных каталогах, а один из путей содержит \\\\?\GlobalRoot, операция завершается ошибкой.  
  
###  <a name="Recommendations"></a> Для чего использовать присоединение?  
В пределах одного экземпляра базы данных рекомендуется перемещать с помощью процедуры планового перемещения `ALTER DATABASE`, а не с помощью операций отсоединения и присоединения. Дополнительные сведения см. в статье [Move User Databases](../../relational-databases/databases/move-user-databases.md). 
 
Мы не рекомендуем использовать отсоединение и присоединение для резервного копирования и восстановления, так как резервные копии журналов транзакций отсутствуют, а файлы могут быть случайно удалены.
  
###  <a name="Security"></a> безопасность  
Разрешения на доступ к файлам устанавливаются во время выполнения определенных операций с базами данных, включая отсоединение и присоединение баз данных. Дополнительные сведения о разрешениях на доступ к файлам, настраиваемых при отсоединении и присоединении базы данных см. в разделе [Защита данных и файлов журналов](https://technet.microsoft.com/library/ms189128.aspx) электронной документации по [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (документация актуальна). 
  
Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код. Дополнительные сведения о присоединении баз данных и сведения об изменениях, вносимых при присоединении баз данных в метаданные, см. в статье [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
####  <a name="Permissions"></a> Permissions  
Требуется разрешение `CREATE DATABASE`, `CREATE ANY DATABASE` или `ALTER ANY DATABASE`.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  

### <a name="to-attach-a-database"></a>Присоединение базы данных  
  
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обозревателе объектов [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]подключитесь к экземпляру компонента и разверните его представление в SSMS.  
  
2.  Щелкните правой кнопкой мыши узел **Базы данных** и выберите команду **Присоединить**.  
  
3.  Чтобы указать присоединяемую базу данных, в диалоговом окне **Присоединение баз данных** нажмите кнопку **Добавить**, в диалоговом окне **Расположение файлов базы данных** выберите диск, на котором находится база данных, и разверните дерево каталогов, чтобы найти и выбрать MDF-файл, например:  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > Trying to select a database that is already attached generates an error.  
  
     **Databases to attach**  
     Displays information about the selected databases.  
  
     \<no column header>  
     Displays an icon indicating the status of the attach operation. The possible icons are described in the **Status** description, below).  
  
     **MDF File Location**  
     Displays the path and file name of the selected MDF file.  
  
     **Database Name**  
     Displays the name of the database.  
  
     **Attach As**  
     Optionally, specifies a different name for the database to attach as.  
  
     **Owner**  
     Provides a drop-down list of possible database owners from which you can optionally select a different owner.  
  
     **Status**  
     Displays the status of the database according to the following table.  
  
    |Значок|Текст состояния|Описание|  
    |----------|-----------------|-----------------|  
    |(Нет значка)|(Нет текста)|Операция присоединения не была запущена или находится в режиме ожидания для этого объекта. Это состояние по умолчанию при открытии диалогового окна.|  
    |Зеленый, указывающий направо треугольник|Выполняется|Операция присоединения была запущена, но не завершена.|  
    |Зеленый флажок|Успешно|Объект успешно присоединен.|  
    |Красный кружок с белым крестом внутри|Ошибка|При выполнении операции присоединения возникла ошибка, и операция не была успешно завершена.|  
    |Кружок с двумя черными квадратами (слева и справа) и двумя белыми квадратами (сверху и снизу)|Остановлена|Операция присоединения не была успешно завершена, т.к. пользователь остановил операцию.|  
    |Кружок, содержащий изогнутую стрелку, указывающую в направлении против часовой стрелки|Выполнен откат|Операция присоединения была успешной, но был выполнен ее откат из-за ошибки, возникшей при вложении другого объекта.|  
  
     **Message**  
     Displays either a blank message or a "File not found" hyperlink.  
  
     **Add**  
     Find the necessary main database files. When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.  
  
     **Remove**  
     Removes the selected file from the **Databases to attach** grid.  
  
     **"** *<database_name>* **" database details**  
     Displays the names of the files to be attached. To verify or change the pathname of a file, click the **Browse** button (**...**).  
  
    > [!NOTE]  
    > If a file does not exist, the **Message** column displays "Not found." If a log file is not found, it exists in another directory or has been deleted. You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid. If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.  
  
     **Original File Name**  
     Displays the name of the attached file belonging to the database.  
  
     **File Type**  
     Indicates the type of file, **Data** or **Log**.  
  
     **Current File Path**  
     Displays the path to the selected database file. The path can be edited manually.  
  
     **Message**  
     Displays either a blank message or a "**File not found**" hyperlink.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
### <a name="to-attach-a-database"></a>Присоединение базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Выполните инструкцию [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) с предложением `FOR ATTACH`.  
  
     Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере производится присоединение файлов базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] с ее последующим переименованием в `MyAdventureWorks`.  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > Кроме того, можно вызвать хранимую процедуру [sp_attach_db](../../relational-databases/system-stored-procedures/sp-attach-db-transact-sql.md) или [sp_attach_single_file_db](../../relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql.md) . Но эти расширенные хранимые процедуры в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]будут удалены. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого рекомендуется использовать `CREATE DATABASE ... FOR ATTACH` .  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После обновления базы данных SQL Server  
После обновления базы данных при помощи описанного метода присоединения, эта база данных сразу становится доступной, после чего обновляется автоматически. Если база данных содержит полнотекстовые индексы, то в процессе обновления будет произведен их импорт, сброс или перестроение в зависимости от установленного значения свойства сервера **Режим обновления полнотекстового каталога** . Если при обновлении выбран режим **Импортировать** или **Перестроить**, то полнотекстовые индексы во время обновления будут недоступны. В зависимости от объема индексируемых данных процесс импорта может занять несколько часов, а перестроение — в несколько (до десяти) раз больше. Обратите внимание, что если при обновлении выбран режим **Импортировать**, а полнотекстовый каталог недоступен, то связанные с ним полнотекстовые индексы будут перестроены.  
  
Если уровень совместимости пользовательской базы данных до обновления был 100 или выше, после обновления он останется таким же. Если уровень совместимости до обновления был 90, в обновленной базе данных он устанавливается в 100, что является минимально поддерживаемым уровнем совместимости в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
> [!NOTE]
> Для подключения базы данных из экземпляра под управлением [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или более ранней версии, в которой включена система отслеживания измененных данных (CDC), потребуется также выполнить следующую команду, чтобы обновить метаданные системы отслеживания измененных данных (CDC).
  
```sql
USE <database name>
EXEC sys.sp_cdc_vupgrade  
``` 
 
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md) 
 <br>[Управление метаданными при предоставлении доступа к базе данных на другом сервере](manage-metadata-when-making-a-database-available-on-another-server.md)  
 [Отсоединение базы данных](../../relational-databases/databases/detach-a-database.md)  
  
  
