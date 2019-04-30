---
title: Урок 3. Создание учетных данных SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 05afd5377ee1d64a28349b46fbc79a9f048c5577
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63144355"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>Урок 3. Создание учетных данных SQL Server
  На этом занятии вы создадите учетные данные для хранения сведений о безопасности, которые будут использоваться для доступа к учетной записи хранения Windows Azure.  
  
 Учетные данные SQL Server — это объект, который используется для хранения сведений, необходимых для проверки подлинности при подключении к ресурсу вне SQL Server. Учетные данные хранят URI-путь к контейнеру хранилища и значениям ключа подписанного URL-адреса. Для каждого контейнера хранилища, используемого файлом данных или журнала, необходимо создать учетные данные SQL Server, имя которых соответствует пути контейнера.  
  
 Общие сведения об учетных данных см. в разделе [учетные данные &#40;СУБД&#41;](security/authentication-access/credentials-database-engine.md).  
  
> [!IMPORTANT]  
>  Требования для создания учетных данных SQL Server, описанные ниже, характерны для [SQL Server Data Files в Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md) функции. Сведения о создании учетных данных для резервного копирования процессов в службе хранилища Azure, см. в разделе [занятии 2: Создание учетных данных SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md).  
  
 Для создания учетных данных SQL Server выполните следующие действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  В обозревателе объектов подключитесь к экземпляру установленного компонента Database Engine.  
  
3.  На панели инструментов Стандартная выберите пункт Создать запрос.  
  
4.  Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените). Следующая инструкция создаст учетные данные SQL Server для хранения сертификата общего доступа контейнера хранилища.  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     Подробные сведения см. в разделе [CREATE CREDENTIAL &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-credential-transact-sql) в электронной документации по SQL Server.  
  
5.  Чтобы увидеть все доступные учетные данные, можно выполнить следующую инструкцию в окне запроса:  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     Дополнительные сведения о sys.credentials см. в разделе [sys.credentials &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) в электронной документации по SQL Server.  
  
 **Следующее занятие:**  
  
 [Занятие 4. Создание базы данных в хранилище Windows Azure](lesson-3-database-backup-to-url.md)  
  
  
