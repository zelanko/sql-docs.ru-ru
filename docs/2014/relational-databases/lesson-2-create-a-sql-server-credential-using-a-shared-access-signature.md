---
title: Занятие 3. Создание учетных данных SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 61a25d1f4e86204d05b3be6bf2a5dbc8cd0474b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "70153833"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>Занятие 3. Создание учетных данных SQL Server
  На этом занятии будут созданы учетные данные для хранения сведений о безопасности, используемых для доступа к учетной записи хранения Azure.  
  
 Учетные данные SQL Server — это объект, который используется для хранения сведений, необходимых для проверки подлинности при подключении к ресурсу вне SQL Server. Учетные данные хранят URI-путь к контейнеру хранилища и значениям ключа подписанного URL-адреса. Для каждого контейнера хранилища, используемого файлом данных или журнала, необходимо создать учетные данные SQL Server, имя которых соответствует пути контейнера.  
  
 Общие сведения об учетных данных см. в разделе [учетные данные &#40;ядро СУБД&#41;](security/authentication-access/credentials-database-engine.md).  
  
> [!IMPORTANT]  
>  Требования к созданию учетных данных SQL Server, описанных ниже, относятся к [SQL Serverным файлам данных в Azure](databases/sql-server-data-files-in-microsoft-azure.md) . Сведения о создании учетных данных для резервного копирования процессов в хранилище Azure см. в разделе [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md).  
  
 Для создания учетных данных SQL Server выполните следующие действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  В обозревателе объектов подключитесь к экземпляру установленного компонента Database Engine.  
  
3.  На панели инструментов Стандартная выберите пункт Создать запрос.  
  
4.  Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените). Следующая инструкция создаст SQL Server учетные данные для хранения сертификата общего доступа контейнера хранилища.  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     Дополнительные сведения см. в разделе [Создание учетных данных &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) в Электронная документация на SQL Server.  
  
5.  Чтобы увидеть все доступные учетные данные, можно выполнить следующую инструкцию в окне запроса:  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     Дополнительные сведения об sys. Credentials см. в разделе [sys. credentials &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) в Электронная документация на SQL Server.  
  
 **Следующее занятие:**  
  
 [Занятие 4. Создание базы данных в службе хранилища Azure](lesson-3-database-backup-to-url.md)  
  
  
