---
title: "Автоматическая установка служб R SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 14
---
# Автоматическая установка служб R SQL Server
    
Прежде чем начать процесс установки, обратите внимание эти требования.

+ Необходимо установить компонент database engine на каждом экземпляре, где будет использоваться службами R (в базы данных) в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
+ При выполнении автономную установку, необходимо заранее загрузить необходимые компоненты R и скопировать их в локальную папку. Адреса загрузки в разделе [Установка компонентов R без доступа к Интернету](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).   
+ Новый параметр */IACCEPTROPENLICENSETERMS*, которое указывает, что вы приняли условия лицензионного соглашения по использованию компонентов R с открытым исходным. Если этот параметр не будет включен в командную строку, установка завершится неудачей.  
  
## Выполнение автоматической установки служб R (в базе данных)  
 В следующем примере показано минимальные необходимые компоненты для указания в командной строке, выполняя автоматическую установку служб R в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
###  <a name="bkmk_Unattended"></a>  
  
1.  Выполните следующую команду из командной строки с повышенными привилегиями:  
  
    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,AdvancedAnalytics /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS  
    ```  
  
2.  После установки, в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], выполните следующую команду, чтобы включить эту функцию.  
  
    ```  
    Exec sp_configure  'external scripts enabled', 1  
    Reconfigure  with  override  
  
    ```  
  
    > [!NOTE]  
    >  Вам нужно явно включить компонент ядра; в противном случае невозможно будет вызывать скрипты R, даже если этот компонент был установлен и настроен программой установки.  
  
3.  Повторно запустите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Связанная служба [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] также будет автоматически перезагружена.  
  
## См. также:  
 [Устранение неполадок при установке служб R](../Topic/Troubleshooting%20R%20Services%20Setup.md)  
  
  