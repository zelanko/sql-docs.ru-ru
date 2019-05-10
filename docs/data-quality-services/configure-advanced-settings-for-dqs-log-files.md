---
title: Настройка дополнительных параметров для файлов журнала DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- log files,advanced settings
- dqs log files,advanced settings
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a18665df70dae12db276e6d6af80ac618a0ea24c
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65486467"
---
# <a name="configure-advanced-settings-for-dqs-log-files"></a>Configure Advanced Settings for DQS Log Files

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этом разделе описано, как настроить дополнительные параметры файлов журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] и [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , такие как скользящий предельный размер файла для файлов журнала, шаблон метки времени для событий и т. д.  
  
> [!NOTE]  
>  Эти действия нельзя выполнить с помощью приложения [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], они предназначены только для продвинутых пользователей.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
  
-   Учетная запись Windows должна быть членом предопределенной роли сервера sysadmin на этом экземпляре SQL Server для изменения параметров конфигурации в таблице A_CONFIGURATION базы данных DQS_MAIN.  
  
-   Чтобы настраивать параметры журналов [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , необходимо быть членом группы администраторов на компьютере, где изменяется файл DQLog.Client.xml.  
  
##  <a name="DQSServer"></a> Настройка параметров журнала сервера DQS  
 Параметры журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] представлены в формате XML в столбце **VALUE** строки **ServerLogging** в таблице A_CONFIGURATION базы данных DQS_MAIN. Вы можете выполнить следующий SQL-запрос для просмотра сведений о конфигурации:  
  
```  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
```  
  
 Необходимо обновить соответствующие сведения в столбце **VALUE** строки **ServerLogging** , чтобы изменить параметры конфигурации для журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . В этом примере обновляются параметры журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , устанавливается скользящий предел файла данных равным 25 000 KБ (по умолчанию он равен 20 000 KБ).  
  
1.  Запустите среду Microsoft SQL Server Management Studio и подключитесь к соответствующему экземпляру SQL Server.  
  
2.  В обозревателе объектов щелкните сервер правой кнопкой мыши и выберите команду **Создать запрос**.  
  
3.  В окно редактора запросов скопируйте следующие инструкции SQL:  
  
    ```  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  Нажмите клавишу F5, чтобы выполнить инструкции. Откройте область **Результаты** , чтобы удостовериться в успешном выполнении инструкций.  
  
5.  Чтобы применить изменения, внесенные в конфигурацию журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , необходимо выполнить следующие инструкции Transact-SQL. Откройте новое окно редактора запросов и вставьте следующие инструкции Transact-SQL:  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
  
    ```  
  
6.  Нажмите клавишу F5, чтобы выполнить инструкции. Откройте область **Результаты** , чтобы удостовериться в успешном выполнении инструкций.  
  
> [!NOTE]  
>  Конфигурация параметров журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] создается автоматически и хранится в файле DQS_MAIN.Log, который обычно находится в папке C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log, если был установлен экземпляр SQL Server по умолчанию. Однако изменения, внесенные непосредственно в этот файл, не сохраняются, они перезаписываются параметрами конфигурации из таблицы A_CONFIGURATION базы данных DQS_MAIN.  
  
##  <a name="DQSClient"></a> Настройка параметров журнала клиента DQS  
 Файл параметров конфигурации журнала [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] DQLog.Client.xml обычно находится в папке C:\Program Files\Microsoft SQL Server\130\Tools\Binn\DQ\config. Содержание этого XML-файла подобно XML-файлу с параметрами конфигурации журнала [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] , который был изменен ранее. Настройка параметров журнала [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] :  
  
1.  Откройте любой редактор XML-файлов или Блокнот с правами администратора.  
  
2.  Откройте файл DQLog.Client.xml в этом редакторе или в Блокноте.  
  
3.  Внесите необходимые изменения и сохраните этот файл, чтобы изменения журнала были применены.  
  
## <a name="see-also"></a>См. также  
 [Настройка степеней серьезности для файлов журнала DQS](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  
