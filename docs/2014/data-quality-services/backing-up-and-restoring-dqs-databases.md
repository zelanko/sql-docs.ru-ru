---
title: Резервное копирование и восстановление баз данных DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 50b051cf2780fc1a94830c461d9ae30674bb7dad
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65481157"
---
# <a name="backing-up-and-restoring-dqs-databases"></a>Резервное копирование и восстановление баз данных DQS
  В этом разделе описывается, как проводить резервное копирование и восстановление баз данных DQS.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо знать пароль для главного ключа базы данных, который вы указывали при установке сервера DQS.  
  
-   Убедитесь, что не существует текущих операций или процессов в DQS. Это можно проверить с помощью экрана **Мониторинг активности** . Дополнительные сведения о работе с этим экраном см. в разделе [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).  
  
-   Убедитесь, что на сервере DQS нет подключенных пользователей.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
  
-   Для выполнения операций резервного копирования и восстановления учетная запись Windows должна быть членом предопределенной роли сервера sysadmin на этом экземпляре SQL Server.  
  
-   Для завершения любых выполняемых операций или остановки каких-либо процессов в службах DQS необходимо быть членом роли dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="BackupRestore"></a> Резервное копирование и восстановление баз данных DQS  
  
1.  Запустите среду Microsoft SQL Server Management Studio и подключитесь к соответствующему экземпляру SQL Server.  
  
2.  В обозревателе объектов разверните узел **Базы данных** .  
  
3.  Создайте резервную копию базы данных DQS_STAGING_DATA. Пошаговые инструкции по резервному копированию базы данных SQL Server см. в разделе [Создание полной резервной копии базы данных &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
4.  Создайте резервную копию базы данных DQS_PROJECTS.  
  
5.  Создайте резервную копию базы данных DQS_MAIN.  
  
6.  Отключитесь от текущего экземпляра SQL Server и подключитесь к экземпляру SQL Server, на котором нужно восстановить эти базы данных.  
  
7.  Восстановите базу данных DQS_MAIN. Пошаговые инструкции по восстановлению базы данных SQL Server см. в разделе [восстановление резервной копии базы данных &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).  
  
8.  Восстановите базу данных DQS_PROJECTS.  
  
9. Восстановите базу данных DQS_STAGING_DATA.  
  
10. В обозревателе объектов щелкните сервер правой кнопкой мыши и выберите команду **Создать запрос**.  
  
11. Скопируйте в окно редактора запросов следующие инструкции SQL, заменив *\<PASSWORD>* на пароль, использованный вами при установке DQS для главного ключа базы данных.  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
  
    ```  
  
12. Нажмите клавишу F5, чтобы выполнить инструкции. Откройте область **Результаты** , чтобы удостовериться в успешном выполнении инструкций.  
  
## <a name="see-also"></a>См. также  
 [Управление базами данных DQS](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
