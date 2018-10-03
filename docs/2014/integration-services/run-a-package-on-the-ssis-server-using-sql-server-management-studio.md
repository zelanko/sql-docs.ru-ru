---
title: Выполнение пакета на сервере служб SSIS с помощью SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7195e8159ed1b4c1fb0092ac07369196403a69f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119234"
---
# <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a>Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio
  После развертывания проекта на сервере служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] пакет можно запускать на сервере.  
  
 В отчетах об операциях можно просматривать сведения о выполненных или выполняемых в данный момент на сервере пакетах. Дополнительные сведения см. в статье [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a>Запуск пакета на сервере с помощью среды SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и подключитесь к экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , в котором содержится каталог служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе объектов разверните узел служб **Integration Services Catalogs** , разверните узел **SSISDB** и перейдите к пакету, содержащемуся в развернутом вами проекте.  
  
3.  Щелкните имя пакета правой кнопкой мыши и выберите команду **Выполнить**.  
  
4.  Настройте выполнение пакета с помощью параметров на вкладках **Параметры**, **Диспетчеры соединений**и **Расширенные** диалогового окна **Выполнение пакета** .  
  
5.  Нажмите кнопку **ОК** , чтобы выполнить пакет.  
  
     -или-  
  
     Используйте хранимую процедуру для запуска пакета. Щелкните **Скрипт** , чтобы сформировать инструкцию Transact-SQL, которая создает и запускает экземпляр выполнения. Инструкция включает в себя вызов хранимых процедур catalog.create_execution, catalog.set_execution_parameter_value и catalog.start_execution. Дополнительные сведения об этих хранимых процедурах см. в разделах [catalog.create_execution (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) и [catalog.start_execution (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).  
  
  
