---
title: Руководство по резервному копированию и восстановлению SQL Server с помощью службы хранилища BLOB-объектов Azure | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 729ec5fc4a811c1c201059ad58086712f6d16f9a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685389"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Руководство по резервному копированию и восстановлению SQL Server с помощью службы хранилища BLOB-объектов Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
С помощью этого руководства вы научитесь создавать и восстанавливать резервные копии, используя службу хранилища BLOB-объектов Azure.  В этом руководстве рассматривается, как создать контейнер больших двоичных объектов Azure, учетные данные для доступа к учетной записи хранения, как записать резервную копию в службу BLOB-объектов, а затем выполнить простое восстановление.
  
### <a name="prerequisites"></a>предварительные требования  
Чтобы выполнить задания этого руководства, необходимо владеть основными понятиями резервного копирования и восстановления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и синтаксисом T-SQL. Для работы с этим руководством требуется учетная запись хранения Azure, среда SQL Server Management Studio (SSMS), доступ к серверу SQL Server и база данных AdventureWorks. Кроме того, учетная запись, используемая для выдачи команд резервного копирования и восстановления, должна находиться в роли базы данных **db_backupoperator** с разрешениями **изменение любых учетных данных**. 

- Получите бесплатную [учетную запись Azure](https://azure.microsoft.com/offers/ms-azr-0044p/).
- Создайте [учетную запись хранения Azure](https://docs.microsoft.com/azure/storage/common/storage-quickstart-create-account?tabs=portal).
- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Скачайте [образцы баз данных AdventureWorks2016](https://docs.microsoft.com/sql/samples/adventureworks-install-configure).
- Назначьте учетной записи пользователя роль [db_backupoperator](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles) и предоставьте разрешения на [изменение любых учетных данных](https://docs.microsoft.com/sql/t-sql/statements/alter-credential-transact-sql). 


## <a name="create-azure-blob-container"></a>Создание контейнера больших двоичных объектов Azure
Контейнер группирует набор больших двоичных объектов. Все большие двоичные объекты должны находиться в контейнере. Учетная запись может содержать неограниченное количество контейнеров, но не менее одного. В контейнере может храниться неограниченное количество больших двоичных объектов. 

Чтобы создать контейнер, выполните следующие действия.

1. Откройте портал Azure. 
1. Перейдите к своей учетной записи хранения. 
   1. Выберите учетную запись хранения, прокрутите вниз до раздела **Службы BLOB-объектов**.
   1. Выберите **BLOB-объекты**, а затем щелкните **+ Контейнер**, чтобы добавить новый контейнер. 
   1. Введите имя контейнера и запишите его. Эти сведения используются в URL-адресе (пути к файлу резервной копии) в инструкциях T-SQL далее в этом руководстве. 
   1. Нажмите кнопку **ОК**. 
    
    ![Создание контейнера](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/new-container.png)


  >[!NOTE]
  >Для резервного копирования и восстановления SQL Server проводится проверка подлинности учетной записи хранилища даже при создании открытого контейнера. Можно также создать контейнер программным образом с помощью REST API. Дополнительные сведения см. в статье [Создание контейнера](https://docs.microsoft.com/rest/api/storageservices/Create-Container).


## <a name="create-a-sql-server-credential"></a>Создание учетных данных SQL Server
Учетные данные SQL Server — это объект, который используется для хранения сведений, необходимых для проверки подлинности при подключении к ресурсу вне SQL Server. В данном случае процессы резервного копирования и восстановления SQL Server используют учетные данные для проверки подлинности в службе хранилища BLOB-объектов Windows Azure. Учетные данные хранят имя учетной записи хранилища и значения **ключа доступа** учетной записи хранилища. После создания учетных данных их необходимо указать в параметре WITH CREDENTIAL при выполнении инструкций BACKUP/RESTORE. Дополнительные сведения об учетных данных см. в статье [Учетные данные (ядро СУБД)](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/credentials-database-engine). 

  >[!IMPORTANT]
  >Требования к созданию учетных данных SQL Server, описанные ниже, характерны для процессов резервного копирования SQL Server ([резервное копирование в SQL Server по URL-адресу](backup-restore/sql-server-backup-to-url.md) и [управляемое резервное копирование SQL Server в Microsoft Azure](backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). При доступе к хранилищу Azure для записи или чтения резервных копий SQL Server использует информацию об имени и ключе доступа учетной записи хранения.

### <a name="access-keys"></a>Ключи доступа
Так как портал Azure по-прежнему открыт, сохраните ключи доступа, необходимые для создания учетных данных. 

1. Перейдите к **учетной записи хранения** на портале Azure. 
1. Прокрутите вниз до раздела **Параметры** и выберите **Ключи доступа**. 
1. Сохраните строку подключения и ключ для дальнейшего использования в этом руководстве. 

   ![Ключи доступа](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/access-keys.png)

### <a name="create-a-sql-server-credential"></a>Создание учетных данных SQL Server
Используя ключ доступа, сохраненный ранее, создайте учетные данные SQL Server, выполнив следующие действия. 

1. Подключитесь к SQL Server, используя SQL Server Management Studio. 
1. Выберите базу данных **AdventureWorks2016** и откройте окно **Новый запрос**. 
1. Скопируйте, вставьте и выполните следующий пример в окне запроса (при необходимости измените). 

  ```sql
  CREATE CREDENTIAL mycredential   
  WITH IDENTITY= 'mystorageaccount', -- this is the name of the storage account you specified when creating a storage account   
  SECRET = '<storage account access key>' -- this should be either the Primary or Secondary Access Key for the storage account 
  ```
1. Выполните инструкцию для создания учетных данных. 

## <a name="backup-database-to-the-windows-azure-blob-storage-service"></a>Резервное копирование базы данных в службу хранилища BLOB-объектов Microsoft Azure
В этом разделе мы выполним полное резервное копирование базы данных в службу хранилища BLOB-объектов Microsoft Azure, используя инструкцию T-SQL. 

1. Подключитесь к SQL Server, используя SQL Server Management Studio. 
1. Выберите базу данных **AdventureWorks2016** и откройте окно **Новый запрос**. 
1. Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените). 

 ```sql
 BACKUP DATABASE[AdventureWorks2016] 
 TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2016.bak' 
 /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/ 
 WITH CREDENTIAL = 'mycredential';
 /* name of the credential you created in the previous step */ 
 GO
 ```
1. Выполните инструкцию для резервного копирования вашей базы данных AdventureWorks2016 на URL-адрес. 

 
## <a name="restore-database-from-windows-azure-blob-storage-service"></a>Восстановление базы данных из службы хранилища BLOB-объектов Microsoft Azure
В этом разделе мы восстановим полную резервную копию базы данных, используя инструкцию T-SQL. 

1. Подключитесь к SQL Server, используя SQL Server Management Studio. 
1. Откройте окно **Новый запрос**. 
1. Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените). 

 ```sql
 RESTORE DATABASE AdventureWorks2016 
 FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak' 
 WITH CREDENTIAL = 'mycredential',
 STATS = 5 -- use this to see monitor the progress
 GO
 ``` 

## <a name="see-also"></a>См. также раздел 
Чтобы разобраться в концепциях и рекомендациях использования службы хранилища BLOB-объектов Azure для резервного копирования [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], рекомендуется изучить перечисленные ниже материалы.  
  
-   [Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
-   [Архивация в SQL Server по URL-адресу — рекомендации и устранение неполадок](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
