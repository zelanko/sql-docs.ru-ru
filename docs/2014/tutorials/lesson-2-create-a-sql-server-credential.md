---
title: 'Занятие 2: Создание учетных данных SQL Server | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 9bac1f166472fa6f4285779f2054d7121133693f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194574"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Lesson 2: Create a SQL Server Credential
  **Учетные данные.** Учетные данные [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] являются объектом, который используется для хранения информации о проверке подлинности, необходимой для подключения к ресурсу за пределами SQL Server.  Здесь [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] процессы резервного копирования и восстановления используют учетные данные для проверки подлинности в службе хранилища больших двоичных объектов Windows Azure. Учетные данные хранят имя учетной записи хранилища и значения **ключа доступа** учетной записи хранилища. После создания учетных данных их необходимо указать в параметре WITH CREDENTIAL при выполнении инструкций BACKUP/RESTORE. Дополнительную информацию о просмотре, копировании или повторном создании учетной записи хранилища **access keys**см. в разделе [Ключи доступа к учетной записи](http://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Общие сведения об учетных данных см. в разделе [учетные данные](../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 Сведения о других примерах использования учетных данных, см. в разделе [создание прокси-агента SQL Server](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
> [!IMPORTANT]  
>  Требования для создания учетных данных SQL Server, описанные ниже, характерны для процессов резервного копирования SQL Server ([SQL Server Backup to URL-адрес](../relational-databases/backup-restore/sql-server-backup-to-url.md), и [SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server, при доступе к хранилищу Azure для записи или чтения резервных копий, использует информацию об имени и ключе доступа учетной записи хранилища.  Дополнительные сведения о создании учетных данных для хранения файлов базы данных в хранилище Azure, см. в разделе [занятия 3: создание учетных данных SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>Создание учетных данных SQL Server  
 Для создания учетных данных SQL Server выполните следующие действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine, на котором установлена база данных AdventureWorks2012, или воспользуйтесь собственной базой данных, запланированной для усвоения материала этого учебника.  
  
3.  На панели инструментов **Стандартная** выберите пункт **Создать запрос**.  
  
4.  Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените).  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' – this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' – this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![Сопоставление учетной записи хранилища с учетными данными sql](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "сопоставление учетной записи хранилища с учетными данными sql")  
  
5.  Проверьте инструкцию T-SQL и нажмите **Выполнить**.  
  
 Дополнительные сведения о службе хранилища больших двоичных объектов Windows Azure для резервного копирования основные понятия и требования, см. в разделе [SQL Server Backup and Restore with Windows Azure Blob Storage Service](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Следующее занятие  
 [Занятие 3: Запись полной резервной копии в Windows Azure Blob Storage Service](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).  
  
  
