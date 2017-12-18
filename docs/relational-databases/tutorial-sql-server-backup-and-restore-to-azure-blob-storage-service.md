---
title: "Руководство по резервному копированию и восстановлению SQL Server с помощью службы хранилища BLOB-объектов Azure | Документация Майкрософт"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016 Preview
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 87ab0fafc43294cd0d9178f966fd7e819a2416d3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Руководство по резервному копированию и восстановлению SQL Server с помощью службы хранилища BLOB-объектов Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] С помощью этого руководства вы научитесь создавать и восстанавливать резервные копии, используя службу хранилища BLOB-объектов Azure.  
  
## <a name="what-you-will-learn"></a>Новые знания  
В этом руководстве показано, как создать учетную запись хранения, контейнер больших двоичных объектов, учетные данные для доступа к учетной записи хранения, как записать резервную копию в службу хранилища BLOB-объектов и выполнить простое восстановление. Учебник разделен на четыре занятия.  
  
[Занятие 1. Создание объектов хранения Azure](http://msdn.microsoft.com/library/74edd1fd-ab00-46f7-9e29-7ba3f1a446c5)  
На этом занятии вы создадите учетную запись хранения Azure и контейнер больших двоичных объектов.  
  
[Занятие 2. Создание учетных данных SQL Server](http://msdn.microsoft.com/library/64f8805c-1ddc-4c96-a47c-22917d12e1ab)  
На этом занятии вы создадите учетные данные для хранения сведений о безопасности, которые будут использоваться для доступа к учетной записи хранения Azure.  
  
[Занятие 3. Запись полной резервной копии базы данных в службу хранилища BLOB-объектов Azure](http://msdn.microsoft.com/library/454c8296-64e9-46ed-b141-5ebfbc8a4fe2)  
На этом занятии вам предстоит выполнить инструкцию Т-SQL для записи резервной копии базы данных AdventureWorks2012 в службу хранилища BLOB-объектов Azure.  
  
[Занятие 4. Восстановление базы данных из полной резервной копии](http://msdn.microsoft.com/library/580f76e6-9802-4abc-9043-db6de592c733)  
На этом занятии также предстоит выполнить инструкцию T-SQL для восстановления из резервной копии базы данных, созданной на предыдущем занятии.  
  
### <a name="requirements"></a>Требования  
Чтобы выполнить задания этого руководства, необходимо владеть основными понятиями резервного копирования и восстановления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и синтаксисом T-SQL. Для работы с этим учебником должны быть выполнены следующие требования.  
  
-   Установленный экземпляр [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] и база данных AdventureWorks2012.  
  
    Экземпляр SQL Server может быть установлен на локальном компьютере или в виртуальной машине Azure.  
  
    Вместо базы данных AdventureWorks2012 можно использовать пользовательскую базу данных, соответственно изменив синтаксис инструкций T-SQL.  
  
-   Учетная запись пользователя, применяемая для выдачи команды BACKUP или RESTORE, должна находиться в роли базы данных **db_backup operator** с разрешениями **Изменение любых учетных данных**.  
  
### <a name="additional-reading"></a>Дополнительные материалы  
Чтобы разобраться в концепциях и предпочтительных методах использования службы хранилища BLOB-объектов Azure для резервного копирования [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], рекомендуется изучить перечисленные ниже материалы.  
  
1.  [Резервное копирование и восстановление SQL Server с помощью службы хранилища Blob-объектов Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
## <a name="see-also"></a>См. также:  
[Резервное копирование и восстановление SQL Server с помощью службы хранилища Blob-объектов Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)

