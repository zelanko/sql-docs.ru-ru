---
title: Занятие 2. Создание политики в контейнере и создание ключа подписи общего доступа (SAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 80bd9c253adfcf1d1a677953fef183d9109534ef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75231815"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a>Занятие 2. Создание политики в контейнере ключа и ключа подписанного URL-адреса
  На этом занятии вы узнаете, как создать политику в контейнере больших двоичных объектов, а также сформировать ключ SAS.  
  
 Сохраненная политика доступа предоставляет дополнительный уровень контроля над подписанными URL-адресами на стороне сервера. Подписанный URL-адрес — URI, который предоставляет ограниченные права доступа к контейнерам, большим двоичным объектам, очередям и таблицам. При использовании этого расширения необходимо создать политику в контейнере с правами на чтение, запись и перечисление.  
  
 Вы можете создать политику и подписанный URL-адрес с помощью одного из следующих методов:  
  
-   Azure REST API Operations: [Создание контейнера](https://msdn.microsoft.com/library/azure/dd179468.aspx), [Настройка ACL контейнера](https://msdn.microsoft.com/library/azure/dd179391.aspx)и [Получение списка ACL контейнера](https://msdn.microsoft.com/library/azure/dd179469.aspx).  
  
-   [Метод CloudBlobContainer. GetSharedAccessSignature](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature) в пакете SDK для Azure.  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   Сторонний инструмент Azure Explorer, например [Обозреватель службы хранилища Azure](https://azurestorageexplorer.codeplex.com/).  
  
 **Следующее занятие:**  
  
 [Урок 3. Создание учетных данных SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
