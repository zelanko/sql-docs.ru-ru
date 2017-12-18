---
title: "Занятие 3. Резервное копирование базы данных по URL-адресу | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
caps.latest.revision: "16"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f63e84d8c22b5c88214cc4d85a6bebf572c41430
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-3-database-backup-to-url"></a>Занятие 3. резервное копирование базы данных по URL-адресу
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] На этом занятии выполняется резервное копирование базы данных AdventureWorks2014 в локальном экземпляре SQL Server 2016 в контейнер Azure, созданный на [занятии 1: создание хранимой политики доступа и подписанного URL-адреса в контейнере Azure](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md).  
  
> [!NOTE]  
> Если необходимо выполнить резервное копирование базы данных SQL Server 2012 с пакетом обновления 1 (SP1) и накопительным пакетом обновления 2 или более поздней версии либо базы данных SQL Server 2014 в этот контейнер Azure, можно воспользоваться устаревшим синтаксисом, который описывается [здесь](https://technet.microsoft.com/en-US/library/dn435916(v=sql.120).aspx) . Таким образом можно выполнить резервное копирование по URL-адресу с помощью синтаксиса WITH CREDENTIAL.  
  
Чтобы выполнить резервное копирование в хранилище BLOB-объектов, выполните указанные ниже действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  Откройте новое окно запроса и подключитесь к экземпляру SQL Server 2016 ядра СУБД в виртуальной машине Azure.  
  
3.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окне запроса. Измените URL-адрес в соответствии с именем учетной записи хранения и контейнером, которые были указаны на занятии 1, а затем выполните этот скрипт.  
  
    ```  
  
    -- To permit log backups, before the full database backup, modify the database to use the full recovery model.  
    USE master;  
    ALTER DATABASE AdventureWorks2014  
       SET RECOVERY FULL;  
  
    -- Back up the full AdventureWorks2014 database to the container that you created in Lesson 1  
    BACKUP DATABASE AdventureWorks2014   
       TO URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_onprem.bak'  
  
    ```  
  
4.  Откройте обозреватель объектов и подключитесь к хранилищу Azure с помощью учетной записи хранения и ключа учетной записи.  
  
5.  Разверните узел "Контейнеры", разверните контейнер, созданный на занятии 1, и убедитесь в том, что резервная копия из шага 3 отображается в нем.  
  
    ![Локальный файл резервной копии отображается как большой двоичный объект в контейнере Azure](../relational-databases/media/0d060e51-012f-4c61-ab8d-16d461d0ffad.JPG "Локальный файл резервной копии отображается как большой двоичный объект в контейнере Azure")  
  
**Следующее занятие:**  
  
[Занятие 4. Восстановление базы данных в виртуальной машине с URL-адреса](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
