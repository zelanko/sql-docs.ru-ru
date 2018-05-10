---
title: Установка служб Reporting Services 2016 из командной строки — SSRS | Документы Майкрософт
ms.custom: ''
ms.date: 01/09/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: install-windows
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- command line
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d81e8c8d8b75fd9557afdb99897b543eb8f9a6ff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="install-reporting-services-2016-at-the-command-prompt"></a>Установка служб Reporting Services 2016 из командной строки

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживают установку из командной строки с помощью программы установки SQL Server. В этом разделе приведено несколько примеров установки из командной строки, характерных для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Полное описание параметров командной строки для всех компонентов SQL Server см. в разделе [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Параметры командной строки для надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint в этом разделе не описываются. Дополнительные сведения об установке этой надстройки из командной строки см. в разделе [Установка надстройки с помощью файла rsSharePoint.msi](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint).

##  <a name="bkmk_native_mode"></a> Службы Reporting Services в основном режиме

### <a name="rsinstallmode-native-mode"></a>RSINSTALLMODE (Собственный режим)
 Главный входной параметр для установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — это **/RSINSTALLMODE** . Он имеет два значения: **DefaultNativeMode** и **FilesOnlyMode**  
  
 Если установка включает компонент SQL Server Database Engine, то по умолчанию RSINSTALLMODE имеет значение DefaultNativeMode. В противном случае параметр RSINSTALLMODE по умолчанию имеет значение FilesOnlyMode. Если выбран режим DefaultNativeMode, но установка не включает компонент SQL Server Database Engine, то параметр RSINSTALLMODE автоматически примет значение FilesOnlyMode. Дополнительные сведения о входных параметрах см. в разделе [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).

### <a name="examples-of-native-mode-installation"></a>Примеры установки в собственном режиме

 Приведенный ниже пример устанавливает и настраивает учетные записи для следующих компонентов:  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
-   Агент SQL Server, который необходим для функций подписки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
```  
Setup.exe /q /IACCEPTSQLSERVERLICENSETERMS /ACTION="install" /ERRORREPORTING=1 /UPDATEENABLED="False" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Adv_SSMS,RS" /RSINSTALLMODE="DefaultNativeMode" /SQLSVCACCOUNT="[DOMAIN\ACCOUNT]" /SQLSVCPASSWORD="[PASSWORD]" /AGTSVCACCOUNT="[DOMAIN\ACCOUNT]" /AGTSVCPASSWORD="[PASSWORD]" /SQLSYSADMINACCOUNTS="[DOMAIN\ACCOUNT]"  
```  
  
##  <a name="bkmk_sharepoint_mode"></a> Службы Reporting Services в режиме интеграции с SharePoint  
  
### <a name="rsshpinstallmode-sharepoint-mode"></a>RSSHPINSTALLMODE (режим интеграции с SharePoint)  
 Входной параметр для установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint — это **/RSSHPINSTALLMODE**. Входной параметр имеет одно значение: SharePointFilesOnlyMode. Данный параметр дает указание к установке всех файлов, необходимых для режима интеграции с SharePoint, но по завершении процесса установки потребуется настройка. Дополнительная настройка осуществляется через центр администрирования SharePoint. Дополнительные сведения см. в разделе [Установка первого сервера отчетов в режиме интеграции с SharePoint](http://msdn.microsoft.com/en-us/b29d0f45-0068-4c84-bd7e-5b8a9cd1b538).  
  
### <a name="examples-of-sharepoint-mode-installation"></a>Примеры установки в режиме интеграции с SharePoint  
 В следующем примере рассматривается установка службы компонента SQL Server Database Engine и служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint, а также надстройки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint (RS_SHPWFE).  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 В следующем примере рассматривается только установка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="[PASSWORD]" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
### <a name="examples-of-sharepoint-mode-upgrade"></a>Примеры обновления режима интеграции с SharePoint  
 В следующем примере выполняется обновление служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. **RSUPGRADEPASSWORD** — это пароль существующей учетной записи службы сервера отчетов. Поле RSUPGRADEPASSWORD является обязательным для обновления, если только учетная запись служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не является встроенной.  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[PASSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="[PASSWORD]"  
```  
  
 Далее приведен пример, с помощью которого можно обновить установку в режиме интеграции с SharePoint, в основе которой лежит архитектура общей службы SharePoint. В этом примере используется параметр ALLOWUPGRADEFORSSRSSHAREPOINTMODE. Этот параметр не требуется для обновления предыдущих версий, не основанных на архитектуре общих служб.  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="[PASSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```

## <a name="next-steps"></a>Следующие шаги

[Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
[Параметры SysPrep](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep)   
[Установка Power Pivot из командной строки](http://msdn.microsoft.com/en-us/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
