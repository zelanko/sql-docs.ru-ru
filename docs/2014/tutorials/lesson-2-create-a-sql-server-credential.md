---
title: Занятие 2. Создание учетных данных SQL Server | Документация Майкрософт
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
ms.openlocfilehash: b1a59c1e32773ddc022319a9357ea61802864a77
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53372586"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Занятие 2. Создание учетных данных SQL Server
  **Учетные данные.** Учетные данные [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] являются объектом, который используется для хранения информации о проверке подлинности, которая необходима для подключения к источнику за пределами SQL Server.  В данном случае процессы резервного копирования и восстановления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] используют учетные данные для проверки подлинности в службе хранилища больших двоичных объектов Windows Azure. Учетные данные хранят имя учетной записи хранилища и значения **ключа доступа** учетной записи хранилища. После создания учетных данных их необходимо указать в параметре WITH CREDENTIAL при выполнении инструкций BACKUP/RESTORE. Дополнительную информацию о просмотре, копировании или повторном создании учетной записи хранилища **access keys**см. в разделе [Ключи доступа к учетной записи](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Общие сведения об учетных данных см. в разделе [Учетные данные](../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 Сведения о других примерах использования учетных данных см. в разделе [Создание учетной записи-посредника агента SQL Server](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
> [!IMPORTANT]  
>  Требования к созданию учетных данных SQL Server, описанные ниже, характерны для процессов резервного копирования SQL Server ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md), и [SQL Server Managed  Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server, при доступе к хранилищу Azure для записи или чтения резервных копий, использует информацию об имени и ключе доступа учетной записи хранилища.  Дополнительные сведения о создании учетных данных для хранения файлов базы данных в хранилище Azure, см. в разделе [занятия 3: Создание учетных данных SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>Создание учетных данных SQL Server  
 Для создания учетных данных SQL Server выполните следующие действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  В обозревателе объектов подключитесь к экземпляру компонента Database Engine, на котором установлена база данных AdventureWorks2012, или воспользуйтесь собственной базой данных, запланированной для усвоения материала этого учебника.  
  
3.  На панели инструментов **Стандартная** выберите пункт **Создать запрос**.  
  
4.  Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените).  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![Сопоставление учетной записи хранилища с учетными данными sql](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "сопоставление учетной записи хранилища с учетными данными sql")  
  
5.  Проверьте инструкцию T-SQL и нажмите **Выполнить**.  
  
 Дополнительные сведения о службе хранилища больших двоичных объектов Windows Azure для резервного копирования основные понятия и требования, см. в разделе [Резервное копирование и восстановление SQL Server с помощью службы хранилищ больших двоичных объектов Windows Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Следующее занятие  
 [Занятие 3. Запись полной резервной копии в Windows Azure Blob Storage Service](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).  
  
  
