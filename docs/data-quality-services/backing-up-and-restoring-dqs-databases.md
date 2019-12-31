---
title: Резервное копирование и восстановление баз данных DQS
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 94b2529323e5a075b6fd423fd8c69ece7a0535c0
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75258848"
---
# <a name="backing-up-and-restoring-dqs-databases"></a>Резервное копирование и восстановление баз данных DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этом разделе описывается, как проводить резервное копирование и восстановление баз данных DQS.  
  
##  <a name="BeforeYouBegin"></a>Перед началом  
  
###  <a name="Prerequisites"></a>Требований  
  
-   Необходимо знать пароль для главного ключа базы данных, который вы указывали при установке сервера DQS.  
  
-   Убедитесь, что не существует текущих операций или процессов в DQS. Это можно проверить с помощью экрана **Мониторинг активности** . Дополнительные сведения о работе с этим экраном см. в разделе [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md).  
  
-   Убедитесь, что на сервере DQS нет подключенных пользователей.  
  
###  <a name="Security"></a>Бюллетеня  
  
####  <a name="Permissions"></a>Чтение  
  
-   Для выполнения операций резервного копирования и восстановления учетная запись Windows должна быть членом предопределенной роли сервера sysadmin на этом экземпляре SQL Server.  
  
-   Для завершения любых выполняемых операций или остановки каких-либо процессов в службах DQS необходимо быть членом роли dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="BackupRestore"></a>Резервное копирование и восстановление баз данных DQS  
  
1.  Запустите среду Microsoft SQL Server Management Studio и подключитесь к соответствующему экземпляру SQL Server.  
  
2.  В обозревателе объектов разверните узел **Базы данных** .  
  
3.  Создайте резервную копию базы данных DQS_STAGING_DATA. Пошаговые инструкции по резервному копированию базы данных SQL Server см. в разделе [Создание полной резервной копии базы данных &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
4.  Создайте резервную копию базы данных DQS_PROJECTS.  
  
5.  Создайте резервную копию базы данных DQS_MAIN.  
  
6.  Отключитесь от текущего экземпляра SQL Server и подключитесь к экземпляру SQL Server, на котором нужно восстановить эти базы данных.  
  
7.  Восстановите базу данных DQS_MAIN. Пошаговые инструкции по восстановлению базы данных SQL Server см. в разделе [Восстановление резервной копии базы данных с помощью среды SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).  
  
8.  Восстановите базу данных DQS_PROJECTS.  
  
9. Восстановите базу данных DQS_STAGING_DATA.  
  
10. В обозревателе объектов щелкните сервер правой кнопкой мыши и выберите команду **Создать запрос**.  
  
11. В окне редактора запросов скопируйте следующие инструкции SQL и замените * \<Password>* паролем, указанным при установке DQS для главного ключа базы данных.  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
  
    ```  
  
12. Нажмите клавишу F5, чтобы выполнить инструкции. Проверьте панель **результатов** , чтобы убедиться, что инструкции выполнены успешно.  
  
## <a name="see-also"></a>См. также  
 [Manage DQS Databases](../data-quality-services/manage-dqs-databases.md)  
  
  
