---
title: "Перенос базы данных с помощью функций отсоединения и присоединения (Transact-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database attaching [SQL Server]
- moving databases [SQL Server]
- database detaching [SQL Server]
- relocating databases [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 6732a431-cdef-4f1e-9262-4ac3b77c275e
caps.latest.revision: 47
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e4604a9d4da9360607e31d31b3f160bc0bff2eac
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="move-a-database-using-detach-and-attach-transact-sql"></a>Перенос базы данных путем отсоединения и присоединения (язык Transact-SQL)
  В этом разделе описывается перемещение отсоединенной базы данных в другое местоположение и ее повторное присоединение к тому же или другому экземпляру сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Однако рекомендуется переносить базы данных с помощью процедуры запланированного переноса ALTER DATABASE, а не путем отсоединения и присоединения. Дополнительные сведения см. в статье [Move User Databases](../../relational-databases/databases/move-user-databases.md).  
  
> [!IMPORTANT]  
>  Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Перед тем как использовать базу данных, полученную из неизвестного или ненадежного источника, выполните на тестовом сервере инструкцию [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) для этой базы данных, а также изучите исходный код в базе данных, например хранимые процедуры и другой пользовательский код.  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-move-a-database-by-using-detach-and-attach"></a>Перемещение базы данных при помощи операций отсоединения и присоединения  
  
1.  Отсоединение базы данных. Дополнительные сведения см. в разделе [Отсоединение базы данных](../../relational-databases/databases/detach-a-database.md).  
  
2.  Переместите в «Проводнике» или окне командной строки файлы отсоединенной базы данных и журналов в новое место.  
  
    > [!NOTE]  
    >  Если база данных включает только один файл небольшого размера, для ее перемещения можно использовать электронную почту.  
  
     Перенос файлов журналов обязателен, даже если нужно создать новые файлы журналов. В некоторых случаях для повторного присоединения базы данных требуются файлы ее существующих журналов. Поэтому всегда храните все файлы отсоединенных журналов, пока база данных не будет успешно присоединена без них.  
  
    > [!NOTE]  
    >  При попытке присоединить базу данных, не указывая файл журнала, операцией присоединения будет произведен поиск файла журнала в его исходном месте. Если копия журнала все еще хранится в исходном месте, она будет присоединена. Чтобы избежать применения исходного файла журнала, либо укажите путь к новому файлу журнала, либо удалите исходную его копию (после его копирования в новое место).  
  
3.  Присоединение скопированных файлов. Дополнительные сведения см. в статье [Attach a Database](../../relational-databases/databases/attach-a-database.md).  
  
## <a name="example"></a>Пример  
 В следующем примере создается копия базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] с именем `MyAdventureWorks`. Инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] выполняются в окне редактора запросов, подключенном к экземпляру сервера, к которому выполнено присоединение.  
  
1.  Отсоедините базу данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] . Для этого выполните следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'AdventureWorks2012';  
    GO  
    ```  
  
2.  Скопируйте любым образом файлы базы данных (AdventureWorks208R2_Data.mdf и AdventureWorks208R2_log) в папки C:\MySQLServer\AdventureWorks208R2_Data.mdf и C:\MySQLServer\AdventureWorks208R2_Log.ldf, соответственно.  
  
    > [!IMPORTANT]  
    >  При работе с производственными базами данных помещайте базу данных и журналы транзакций на отдельные диски.  
  
     При копировании файлов по сети на диск удаленного компьютера укажите имя удаленного места в формате UNC. Имя UNC имеет следующий формат: **\\\\***имя_сервера***\\***имя_общего_хранилища***\\***путь***\\***имя_файла*. Как и при записи файлов на жесткий диск локального компьютера, для записи (или считывания) файла на диск удаленного компьютера учетной запись пользователя, которая используется экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], должны быть предоставлены соответствующие разрешения.  
  
3.  Присоедините перемещенную базу данных и, возможно, ее журнал, выполнив следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Data.mdf'),  
        (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Log.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]только что присоединенная база данных отображается в обозревателе объектов не сразу. Чтобы отобразить базу данных, щелкните в обозревателе объектов пункт **Вид** , а затем **Обновить**. Теперь, раскрыв в обозревателе объектов узел **Базы данных** , можно увидеть в списке присоединенную базу данных.  
  
## <a name="see-also"></a>См. также:  
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
