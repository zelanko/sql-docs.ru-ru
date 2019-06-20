---
title: Создание каталога служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6ed56d36-18d9-40c2-b51f-f2a4c71d1e73
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c9592898521aee296677c195d860dcb6b5e205a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66060102"
---
# <a name="create-the-ssis-catalog"></a>Создание каталога служб SSIS
  После разработки и тестирования пакетов в [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]можно выполнить развертывание проектов, содержащих пакеты, на сервере [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Прежде чем развертывать проекты на сервере служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], необходимо создать каталог `SSISDB` на этом сервере. Программа установки [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] не создает этот каталог автоматически. Его необходимо создать вручную, следуя приведенным ниже инструкциям.  
  
 Вы можете создать каталог SSISDB в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Можно также создать каталог программным способом с помощью Windows PowerShell.  
  
### <a name="to-create-the-ssisdb-catalog-in-sql-server-management-studio"></a>Создание каталога SSISDB в SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Соединитесь с ядром СУБД [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
3.  В обозревателе объектов разверните узел сервера, щелкните правой кнопкой мыши узел **Каталоги служб Integration Services** и выберите пункт **Создать каталог**.  
  
4.  Установите флажок **Включить интеграцию со средой CLR**.  
  
     Каталог использует хранимые процедуры CLR.  
  
5.  Щелкните **Включить автоматическое выполнение хранимой процедуры служб Integration Services при запуске SQL Server** , чтобы хранимая процедура [catalog.startup](/sql/integration-services/system-stored-procedures/catalog-startup) выполнялась каждый раз при перезапуске экземпляра сервера служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
     Хранимая процедура осуществляет обслуживание состояния операций для каталога SSISDB. Она исправляет состояние любых пакетов, выполнявшихся в момент отключения экземпляра сервера служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
6.  Введите пароль и нажмите кнопку **ОК**.  
  
     Этот пароль защищает главный ключ базы данных, используемый для шифрования данных каталога. Сохраните пароль в надежном месте. Рекомендуется также создать резервную копию главного ключа базы данных. Дополнительные сведения см. в статье [Back Up a Database Master Key](../relational-databases/security/encryption/back-up-a-database-master-key.md).  
  
### <a name="to-create-the-ssisdb-catalog-programmatically"></a>Создание каталога SSISDB программным способом  
  
1.  Выполните следующий скрипт PowerShell.  
  
    ```  
    # Load the IntegrationServices Assembly  
    [Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices")  
  
    # Store the IntegrationServices Assembly namespace to avoid typing it every time  
    $ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"  
  
    Write-Host "Connecting to server ..."  
  
    # Create a connection to the server  
    $sqlConnectionString = "Data Source=localhost;Initial Catalog=master;Integrated Security=SSPI;"  
    $sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString  
  
    # Create the Integration Services object  
    $integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection  
  
    # Provision a new SSIS Catalog  
    $catalog = New-Object $ISNamespace".Catalog" ($integrationServices, "SSISDB", "P@assword1")  
    $catalog.Create()  
  
    ```  
  
     Дополнительные примеры использования Windows PowerShell и пространства имен <xref:Microsoft.SqlServer.Management.IntegrationServices> см. в записи блога [SSIS and PowerShell in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539) (Службы SSIS и PowerShell в SQL Server 2012) на сайте blogs.msdn.com. Общие сведения о пространстве имен и примеры кода см. в записи блога [Обзор модели управляемых объектов каталога служб SSIS](https://go.microsoft.com/fwlink/?LinkId=254267)на сайте blogs.msdn.com.  
  
## <a name="see-also"></a>См. также  
 [Каталог служб SSIS](catalog/ssis-catalog.md)   
 [Резервное копирование, восстановление и перемещение каталога служб SSIS](../../2014/integration-services/backup-restore-and-move-the-ssis-catalog.md)  
  
  
