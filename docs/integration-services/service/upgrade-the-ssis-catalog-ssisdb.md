---
title: "Обновление каталога служб SSIS (SSISDB) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.dbupgradewizard.f1"
ms.assetid: 170c3dc9-f5bf-4599-ae56-d24a620f23e8
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Обновление каталога служб SSIS (SSISDB)
  Используйте мастер обновления SSISDB, чтобы обновить базу данных для каталога служб SSIS (SSISDB), если эта база данных старше текущей версии экземпляра SQL Server. Это случается, если верно любое из следующих условий:  
  
-   База данных восстановлена из более старой версии SQL Server.  
  
-   База данных не была удалена из группы доступности AlwaysOn перед обновлением экземпляра SQL Server. Это препятствует автоматическому обновлению базы данных. Дополнительные сведения см. в разделе [Upgrading SSISDB in an availability group](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Upgrade).  
  
 Мастер может обновить только базу данных на экземпляре локального сервера.  
  
## Обновление каталога служб SSIS (SSISDB) посредством запуска мастера обновления SSISDB  
  
1.  Выполните архивацию базы данных каталога служб SSIS (SSISDB).  
  
2.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]разверните локальный сервер, а затем — **Каталоги служб Integration Services**.  
  
3.  Щелкните правой кнопкой мыши **SSISDB**, а затем выберите **Обновление базы данных**, чтобы запустить мастер обновления SSISDB.  
  
     ![Launch the SSISDB upgrade wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-1.png "Launch the SSISDB upgrade wizard")  
  
4.  На странице **Выбор экземпляра** выберите экземпляр SQL Server на локальном сервере.  
  
    > [!IMPORTANT]  
    >  Мастер может обновить только базу данных на экземпляре локального сервера.  
  
     Установите флажок, чтобы указать, что вы выполнили архивацию базы данных SSISDB перед запуском мастера.  
  
     ![Select the server in the SSISDB Upgrade Wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-2.png "Select the server in the SSISDB Upgrade Wizard")  
  
5.  Выберите **Обновить** , чтобы обновить базу данных каталога служб SSIS.  
  
6.  Просмотрите результаты на странице **Результаты** .  
  
     ![Review the results in the SSISDB Upgrade Wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-3.png "Review the results in the SSISDB Upgrade Wizard")  
  
  