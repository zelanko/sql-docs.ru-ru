---
title: "Обновление сборок SQLCLR после установки обновлений .NET Framework | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1a008cc-7e6b-4655-a869-bd429f986400
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6db39bd532f38aea27f8e2860757a5f174f481d7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="upgrade-sqlclr-assemblies-after-net-framework-update"></a>Обновление сборок SQLCLR после загрузки обновлений .NET Framework
  [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) представляют собой набор процедур среды SQLCR, которые ссылаются на сборки Microsoft .NET Framework 4. Установка на компьютер любых обновлений .NET Framework, оказывающих влияние на какую-либо подобную сборку, приводит к изменениям в Module Version ID (MVID) сборки в глобальном кэше сборок (GAC). Это приводит к возникновению рассогласования между идентификаторами MVID используемой сборки в глобальном кэше сборок и сборки, входящей в состав [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Если после обновления платформы .NET Framework необходимо перезагрузить компьютер с [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , то измененные сборки SQLCLR обновляются автоматически, чтобы устранить рассогласование идентификаторов MVID после перезагрузки компьютера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . Однако при обновлениях платформы .NET Framework, не требующих перезагрузки сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , при попытке подключения клиента [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] к серверу [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]происходит ошибка из-за рассогласования идентификаторов MVID сборок.  
  
```  
A new version of .NET was installed on this machine. In order to continue to work with DQS please run dqsinstaller.exe –upgradedlls.  
```  
  
 Чтобы исправить эту неполадку, необходимо обновить измененные сборки SQLCLR в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Для этого запустите файл DQSInstaller.exe с параметром командой строки **upgradedlls** , что позволит пропустить повторное создание баз данных DQS и выполнить только обновления задействованных сборок. Существующие базы знаний, проекты служб DQS и любые другие данные в DQS сохранятся.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Необходимо выполнить вход от имени члена группы администраторов на компьютере [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   Учетная запись пользователя Windows должна входить в предопределенную роль сервера sysadmin на экземпляре SQL Server, где установлен сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
### <a name="to-upgrade-sqlclr-assemblies"></a>Обновление сборок SQLCLR  
  
1.  Откройте командную строку.  
  
2.  В командной строке перейдите в папку, где находится файл DQSInstaller.exe. Если был установлен экземпляр SQL Server по умолчанию, файл DQSInstaller.exe будет находиться в папке C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
    ```  
    dqsinstaller.exe -upgradedlls  
    ```  
  
4.  Остальные шаги совпадают с шагами 2–6 в разделе [Запуск файла DQSInstaller.exe с экрана "Пуск", из меню "Пуск" или из проводника Windows](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) статьи [Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Обновление схемы базы данных DQS после установки обновления SQL Server](../../data-quality-services/install-windows/upgrade-dqs-databases-schema-after-installing-sql-server-update.md)  
  
  
