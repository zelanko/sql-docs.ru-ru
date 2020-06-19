---
title: Занятие 2. Создание учетных данных SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 95118647df945840d306d2f549f9d6b1f9b5c04d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063967"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Урок 2. Создание учетных данных SQL Server
  **Учетные данные**. Учетные данные [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] являются объектом, который используется для хранения информации о проверке подлинности, которая необходима для подключения к источнику за пределами SQL Server.  Здесь [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] процессы резервного копирования и восстановления используют учетные данные для проверки подлинности в службе хранилища BLOB-объектов Azure. Учетные данные хранят имя учетной записи хранилища и значения **ключа доступа** учетной записи хранилища. После создания учетных данных их необходимо указать в параметре WITH CREDENTIAL при выполнении инструкций BACKUP/RESTORE. Дополнительную информацию о просмотре, копировании или повторном создании учетной записи хранилища **access keys**см. в разделе [Ключи доступа к учетной записи](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Общие сведения об учетных данных см. в разделе [учетные данные](../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 Дополнительные сведения о других примерах использования учетных данных см. в статье [создание агент SQL Server прокси-сервера](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
> [!IMPORTANT]  
>  Требования к созданию учетных данных SQL Server, описанных ниже, относятся к SQL Server процессам резервного копирования ([SQL Server резервное копирование на URL-адрес](../relational-databases/backup-restore/sql-server-backup-to-url.md)и [SQL Server управляемого резервного копирования в Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server, при доступе к хранилищу Azure для записи или чтения резервных копий, использует информацию об имени и ключе доступа учетной записи хранилища.  Дополнительную информацию о создании учетных данных для хранения файлов базы данных в хранилище Azure можно узнать в статье [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md).  
  
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
  
     ![сопоставление учетной записи хранилища с учетными данными SQL](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "сопоставление учетной записи хранилища с учетными данными SQL")  
  
5.  Проверьте инструкцию T-SQL и нажмите **Выполнить**.  
  
 Дополнительные сведения о службе хранилища BLOB-объектов Azure для основных понятий и требований для резервного копирования см. [в статье SQL Server резервное копирование и восстановление с помощью службы хранилища BLOB-объектов Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Следующее занятие  
 [Занятие 3. запись полной резервной копии базы данных в службу хранилища BLOB-объектов Azure](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).  
  
  
