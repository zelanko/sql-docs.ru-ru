---
title: Урок 3. Создание учетных данных SQL Server | Документация Майкрософт
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
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153833"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>Урок 3. Создание учетных данных SQL Server
  На этом занятии будут созданы учетные данные для хранения сведений о безопасности, используемых для доступа к учетной записи хранения Azure.  
  
 Учетные данные SQL Server — это объект, который используется для хранения сведений, необходимых для проверки подлинности при подключении к ресурсу вне SQL Server. Учетные данные хранят URI-путь к контейнеру хранилища и значениям ключа подписанного URL-адреса. Для каждого контейнера хранилища, используемого файлом данных или журнала, необходимо создать учетные данные SQL Server, имя которых соответствует пути контейнера.  
  
 Общие сведения об учетных данных см. в разделе [учетные данные &#40;ядро СУБД&#41;](security/authentication-access/credentials-database-engine.md).  
  
> [!IMPORTANT]  
>  Требования к созданию учетных данных SQL Server, описанных ниже, относятся к [SQL Serverным файлам данных в Azure](databases/sql-server-data-files-in-microsoft-azure.md) . Сведения о создании учетных данных для процессов резервного копирования в службе [хранилища Azure см. в разделе занятие 2. Создайте SQL Server учетные](../tutorials/lesson-2-create-a-sql-server-credential.md)данные.  
  
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
  
     Дополнительные сведения см. в разделе [Создание &#40;учетных данных&#41; Transact-SQL](/sql/t-sql/statements/create-credential-transact-sql) в Электронная документация на SQL Server.  
  
5.  Чтобы увидеть все доступные учетные данные, можно выполнить следующую инструкцию в окне запроса:  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     Дополнительные сведения о sys. Credentials см. в разделе [sys &#40;. Credentials&#41; Transact-SQL](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) в Электронная документация на SQL Server.  
  
 **Следующее занятие:**  
  
 [Занятие 4. Создание базы данных в службе хранилища Azure](lesson-3-database-backup-to-url.md)  
  
  
