---
title: "Занятие 2. Создание учетных данных SQL Server с помощью подписанного URL-адреса | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/25/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f6e88b211fc2a053ffeadb038298a28179a94d88
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-2-create-a-sql-server-credential-using-a-shared-access-signature"></a>Занятие 2. Создание учетных данных SQL Server с помощью подписанного URL-адреса
На этом занятии вы создадите учетные данные для хранения сведений о безопасности, которые будут использоваться SQL Server для выполнения записи в контейнер Azure, созданный на [занятии 1 "Создание хранимой политики доступа и подписанного URL-адреса для контейнера Azure"](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md), и чтения из него.  
  
Учетные данные SQL Server — это объект, который используется для хранения сведений, необходимых для проверки подлинности при подключении к ресурсу вне SQL Server. В учетных данных хранится URI-путь к контейнеру хранилища и подписанный URL-адрес этого контейнера.  
  
> [!NOTE]  
> Если необходимо выполнить резервное копирование базы данных SQL Server 2012 с пакетом обновления 1 (SP1) и накопительным пакетом обновления 2 или более поздней версии либо базы данных SQL Server 2014 в этот контейнер Azure, можно воспользоваться устаревшим синтаксисом, который описывается [здесь](https://technet.microsoft.com/en-US/library/dn435916(v=sql.120).aspx) , чтобы создать учетные данные SQL Server на основе ключа учетной записи хранения.  
  
## <a name="create-sql-server-credential"></a>Создание учетных данных SQL Server  
Чтобы создать учетные данные SQL Server, выполните указанные ниже действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  Откройте новое окно запроса и подключитесь к экземпляру SQL Server 2016 ядра СУБД в локальной среде.  
  
3.  В новом окне запроса вставьте инструкцию CREATE CREDENTIAL с подписанным URL-адресом из занятия 1, а затем выполните скрипт.  
  
    Код скрипта будет выглядеть следующим образом.  
  
    ```Transact-SQL  
  
    USE master  
    CREATE CREDENTIAL 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>' – this name must match the container path, start with https and must not contain a forward slash.  
       WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
       , SECRET = 'sharedaccesssignature' –- this is the shared access signature key that you obtained in Lesson 1.   
    GO  
  
    ```  
  
4.  Чтобы увидеть все доступные учетные данные, можно выполнить следующую инструкцию в окне запроса, подключенном к экземпляру:  
  
    ```Transact-SQL  
    SELECT * from sys.credentials  
    ```  
  
5.  Откройте новое окно запроса и подключитесь к экземпляру SQL Server 2016 ядра СУБД в виртуальной машине Azure.  
  
6.  В новом окне запроса вставьте инструкцию CREATE CREDENTIAL с подписанным URL-адресом из занятия 1, а затем выполните скрипт.  
  
7.  Повторите шаги 5 и 6 для дополнительных экземпляров SQL Server 2016, которые должны иметь доступ к контейнеру Azure.  
  
**Следующее занятие:**  
  
[Занятие 3. Резервное копирование базы данных по URL-адресу](../relational-databases/lesson-3-database-backup-to-url.md)  
  
## <a name="see-also"></a>См. также:  
[Учетные данные (компонент Database Engine)](../relational-databases/security/authentication-access/credentials-database-engine.md)  
[CREATE CREDENTIAL &#40;Transact-SQL&#41;](../t-sql/statements/create-credential-transact-sql.md)  
[sys.credentials (Transact-SQL)](../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  


