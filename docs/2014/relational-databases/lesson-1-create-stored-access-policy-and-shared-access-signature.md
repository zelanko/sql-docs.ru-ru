---
title: Занятие 2. Создание политики для контейнера и создавать ключ подписи общего доступа (SAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7ddcef5d5e0695041742784151103c358a973d55
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806735"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a>Занятие 2. Создание политики в контейнере ключа и ключа подписанного URL-адреса
  На этом занятии вы узнаете, как создать политику в контейнере больших двоичных объектов, а также сформировать ключ SAS.  
  
 Сохраненная политика доступа предоставляет дополнительный уровень контроля над подписанными URL-адресами на стороне сервера. Подписанный URL-адрес — URI, который предоставляет ограниченные права доступа к контейнерам, большим двоичным объектам, очередям и таблицам. При использовании этого расширения необходимо создать политику в контейнере с правами на чтение, запись и перечисление.  
  
 Вы можете создать политику и подписанный URL-адрес с помощью одного из следующих методов:  
  
-   Операции Windows Azure REST API: [Создание контейнера](https://msdn.microsoft.com/library/azure/dd179468.aspx), [задать ACL контейнера](https://msdn.microsoft.com/library/azure/dd179391.aspx), и [получить ACL контейнера](https://msdn.microsoft.com/library/azure/dd179469.aspx).  
  
-   [Метод CloudBlobContainer.GetSharedAccessSignature](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.storageclient.cloudblobcontainer.getsharedaccesssignature.aspx) в Windows Azure SDK.  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   Средство обозревателя Windows Azure независимых производителей, таких как [обозреватель службы хранилища Azure](http://azurestorageexplorer.codeplex.com/).  
  
 **Следующее занятие:**  
  
 [Занятие 3. Создание учетных данных SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
  
