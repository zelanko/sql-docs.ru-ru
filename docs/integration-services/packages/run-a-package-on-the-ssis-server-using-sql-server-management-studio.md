---
title: "Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio
  После развертывания проекта на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакет можно запускать на сервере.  
  
 В отчетах об операциях можно просматривать сведения о выполненных или выполняемых в данный момент на сервере пакетах. Дополнительные сведения см. в статье [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
### Запуск пакета на сервере с помощью среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в котором содержится каталог служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе объектов разверните узел служб **Integration Services Catalogs** , разверните узел **SSISDB** и перейдите к пакету, содержащемуся в развернутом вами проекте.  
  
3.  Щелкните имя пакета правой кнопкой мыши и выберите команду **Выполнить**.  
  
4.  Настройте выполнение пакета с помощью параметров на вкладках **Параметры**, **Диспетчеры соединений**и **Расширенные** диалогового окна **Выполнение пакета** .  
  
5.  Нажмите кнопку **ОК** , чтобы выполнить пакет.  
  
     -или-  
  
     Используйте хранимую процедуру для запуска пакета. Щелкните **Скрипт**, чтобы сформировать инструкцию Transact-SQL, которая создает и запускает экземпляр выполнения. Инструкция включает в себя вызов хранимых процедур catalog.create_execution, catalog.set_execution_parameter_value и catalog.start_execution. Дополнительные сведения об этих хранимых процедурах см. в разделах [catalog.create_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md), [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md) и [catalog.start_execution (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).  
  
  