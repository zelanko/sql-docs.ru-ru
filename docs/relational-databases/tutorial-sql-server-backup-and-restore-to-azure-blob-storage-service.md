---
title: Краткое руководство. Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Azure | Документация Майкрософт
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
ms.openlocfilehash: d3ded19a91aba627a9d69d711a1d1640dc042a56
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893632"
---
# <a name="quickstart-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Краткое руководство. Резервное копирование и восстановление SQL Server с помощью службы хранилищ BLOB-объектов Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
С помощью этого краткого руководства вы научитесь создавать и восстанавливать резервные копии, используя службу хранилища BLOB-объектов Azure.  В этом руководстве рассматривается, как создать контейнер больших двоичных объектов Azure, учетные данные для доступа к учетной записи хранения, как записать резервную копию в службу BLOB-объектов, а затем выполнить простое восстановление.
  
### <a name="prerequisites"></a>предварительные требования  
Чтобы выполнить задания этого руководства, необходимо владеть основными понятиями резервного копирования и восстановления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и синтаксисом T-SQL. Для работы с этим руководством требуется учетная запись хранения Azure, среда SQL Server Management Studio (SSMS), доступ к серверу SQL Server и база данных AdventureWorks. Кроме того, учетная запись, используемая для выдачи команд резервного копирования и восстановления, должна находиться в роли базы данных **db_backupoperator** с разрешениями **изменение любых учетных данных**. 

- Получите бесплатную [учетную запись Azure](https://azure.microsoft.com/offers/ms-azr-0044p/).
- Создайте [учетную запись хранения Azure](https://docs.microsoft.com/azure/storage/common/storage-quickstart-create-account?tabs=portal).
- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Назначьте учетной записи пользователя роль [db_backupoperator](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles) и предоставьте разрешения на [изменение любых учетных данных](https://docs.microsoft.com/sql/t-sql/statements/alter-credential-transact-sql). 


## <a name="create-azure-blob-container"></a>Создание контейнера больших двоичных объектов Azure
Контейнер группирует набор больших двоичных объектов. Все большие двоичные объекты должны находиться в контейнере. Учетная запись может содержать неограниченное количество контейнеров, но не менее одного. В контейнере может храниться неограниченное количество больших двоичных объектов. 

[!INCLUDE[freshInclude](../includes/paragraph-content/fresh-note-steps-feedback.md)]

Чтобы создать контейнер, выполните следующие действия.

1. Откройте портал Azure. 
1. Перейдите к своей учетной записи хранения. 
1. Выберите учетную запись хранения, прокрутите вниз до раздела **Службы BLOB-объектов**.
1. Выберите **BLOB-объекты**, а затем щелкните **+ Контейнер**, чтобы добавить новый контейнер. 
1. Введите имя контейнера и запишите его. Эти сведения используются в URL-адресе (пути к файлу резервной копии) в инструкциях T-SQL далее в этом руководстве. 
1. Нажмите кнопку **ОК**. 
    
    ![Создание контейнера](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/new-container.png)


  > [!NOTE]
  > Для резервного копирования и восстановления SQL Server проводится проверка подлинности учетной записи хранилища даже при создании открытого контейнера. Можно также создать контейнер программным образом с помощью REST API. Дополнительные сведения см. в статье [Создание контейнера](https://docs.microsoft.com/rest/api/storageservices/Create-Container).

## <a name="create-a-test-database"></a>Создание тестовой базы данных 

1. Запустите среду [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) и подключитесь к своему экземпляру SQL Server.
1. Откройте окно **Новый запрос**. 
1. Выполните следующий код Transact-SQL (T-SQL) для создания тестовой базы данных. Обновите узел **Базы данных** в **обозревателе объектов** для отображения новой базы данных. 

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


## <a name="create-a-sql-server-credential"></a>Создание учетных данных SQL Server
Учетные данные SQL Server — это объект, который используется для хранения сведений, необходимых для проверки подлинности при подключении к ресурсу вне SQL Server. В данном случае процессы резервного копирования и восстановления SQL Server используют учетные данные для проверки подлинности в службе хранилища BLOB-объектов Windows Azure. Учетные данные хранят имя учетной записи хранилища и значения **ключа доступа** учетной записи хранилища. После создания учетных данных их необходимо указать в параметре WITH CREDENTIAL при выполнении инструкций BACKUP/RESTORE. Дополнительные сведения об учетных данных см. в статье [Учетные данные (ядро СУБД)](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/credentials-database-engine). 

  > [!IMPORTANT]
  > Требования к созданию учетных данных SQL Server, описанные ниже, характерны для процессов резервного копирования SQL Server ([резервное копирование в SQL Server по URL-адресу](backup-restore/sql-server-backup-to-url.md) и [управляемое резервное копирование SQL Server в Microsoft Azure](backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). При доступе к хранилищу Azure для записи или чтения резервных копий SQL Server использует информацию об имени и ключе доступа учетной записи хранения.

### <a name="access-keys"></a>Ключи доступа
Для создания учетных данных понадобятся ключи доступа для учетной записи хранения. 

1. Перейдите к **учетной записи хранения** на портале Azure. 
1. В разделе **Параметры** выберите **Ключи доступа**. 
1. Сохраните строку подключения и ключ для дальнейшего использования в этом руководстве. 

   ![Ключи доступа](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/access-keys.png)

### <a name="create-a-sql-server-credential"></a>Создание учетных данных SQL Server
Используя ключ доступа, сохраненный ранее, создайте учетные данные SQL Server, выполнив следующие действия. 

1. Подключитесь к SQL Server, используя SQL Server Management Studio. 
1. Выберите базу данных **SQLTestDB** и откройте окно **нового запроса**. 
1. Скопируйте, вставьте и выполните следующий пример в окне запроса (при необходимости измените). 

   ```sql
   CREATE CREDENTIAL mycredential   
   WITH IDENTITY= 'msftutorialstorage', -- this is the name of the storage account you specified when creating a storage account   
   SECRET = '<storage account access key>' -- this should be either the Primary or Secondary Access Key for the storage account 
   ```

1. Выполните инструкцию для создания учетных данных. 

## <a name="back-up-database-to-the-windows-azure-blob-storage-service"></a>Резервное копирование базы данных в службу хранилища BLOB-объектов Microsoft Azure
В этом разделе мы выполним полное резервное копирование базы данных в службу хранилища BLOB-объектов Microsoft Azure, используя инструкцию T-SQL. 

1. Подключитесь к SQL Server, используя SQL Server Management Studio. 
1. Выберите базу данных **SQLTestDB** и откройте окно **нового запроса**. 
1. Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените). 

     ```sql
     BACKUP DATABASE [SQLTestDB] 
     TO URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/SQLTestDB.bak' 
     /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/ 
     WITH CREDENTIAL = 'mycredential';
     /* name of the credential you created in the previous step */ 
     GO
     ```

1. Выполните инструкцию для резервного копирования вашей базы данных SQLTestDB на URL-адрес. 

 
## <a name="restore-database-from-windows-azure-blob-storage-service"></a>Восстановление базы данных из службы хранилища BLOB-объектов Microsoft Azure
В этом разделе мы восстановим полную резервную копию базы данных, используя инструкцию T-SQL. 

1. Подключитесь к SQL Server, используя SQL Server Management Studio. 
1. Откройте окно **Новый запрос**. 
1. Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените). 

 ```sql
 RESTORE DATABASE [SQLTestDB] 
 FROM URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/SQLTestDB.bak' 
 WITH CREDENTIAL = 'mycredential',
 STATS = 5 -- use this to see monitor the progress
 GO
 ``` 

## <a name="see-also"></a>См. также раздел 
Чтобы разобраться в концепциях и рекомендациях использования службы хранилища BLOB-объектов Azure для резервного копирования [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], рекомендуется изучить перечисленные ниже материалы.  
  
-   [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
-   [Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
