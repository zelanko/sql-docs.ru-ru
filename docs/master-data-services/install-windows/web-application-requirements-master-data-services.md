---
title: "Требования веб-приложений (службы Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "службы master data services"
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
caps.latest.revision: 40
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 38
---
# Требования веб-приложений (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] — это веб-приложение, размещенное в службах IIS. [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] работает только в Internet Explorer (IE) 9 или более поздней версии. Internet Explorer 8 и более ранние версии, а также Microsoft Edge и Chrome не поддерживаются.  
  
 С помощью программы [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] создайте и настройте веб-приложение для размещения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] настраивает службы IIS на локальном компьютере, поэтому она лучше всего подходит для начальных задач веб-конфигурации. Например, можно настроить службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с одним веб-приложением [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или первое веб-приложение в конфигурации с масштабным развертыванием служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. С помощью средств IIS выполняются более сложные задачи, например настройка нескольких веб-серверов в конфигурации с масштабным развертыванием.  
  
> [!NOTE]  
>  Любой компьютер, на котором устанавливаются компоненты [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], должен иметь соответствующие лицензии. Дополнительные сведения см. в лицензионном соглашении.  
  
## Требования  
  
### Операционная система  
 Прежде чем приступить к установке служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], ознакомьтесь со следующими требованиями:    
    
-   [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)    
  
### Microsoft Silverlight  
 Для работы в веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] на клиентском компьютере необходимо установить Silverlight 5. Если требуемая версия Silverlight отсутствует, то при переходе к той части веб-приложения, которая использует Silverlight, программа предложит установить Silverlight. Вы можете установить Silverlight 5 [с этой веб-страницы](http://go.microsoft.com/fwlink/?LinkId=243096).  
  
### Роль и службы ролей  
 В Windows Server 2012 или Windows Server 2012 R2 можно использовать **Диспетчер сервера**, доступный в консоли управления (MMC), для установки роли **Веб-сервер (IIS)** и следующих необходимых служб ролей.  
 
 
> [!IMPORTANT]  
>**Функция сжатия динамического содержимого** IIS по умолчанию включена. Это позволяет существенно уменьшить размер XML-ответа и количество операций сетевого ввода/вывода, однако использование ЦП увеличивается.  Дополнительные сведения см. в разделе **Улучшенная производительность [CTP 2.0]** статьи [Новые возможности Master Data Services (MDS)](../../master-data-services/what-s-new-in-master-data-services-mds.md).  
  
||  
|-|  
|Службы IIS<br /><br /> Средства управления веб-сайтом<br /><br /> Консоль управления (IIS)<br /><br /> Веб-службы Интернета<br /><br /> Разработка приложений<br /><br /> Расширяемость платформы .NET версии 3.5<br /><br /> Расширяемость платформы .NET версии 4.5<br /><br /> ASP.NET 3.5<br /><br /> ASP.NET 4.5<br /><br /> Расширения ISAPI<br /><br /> Фильтры ISAPI<br /><br /> Общие функции HTTP<br /><br /> Документ по умолчанию<br /><br /> Обзор каталога<br /><br /> Ошибки HTTP<br /><br /> Статическое содержимое<br /><br /> [Примечание: не устанавливайте протокол публикации WebDAV.]<br /><br /> Исправность и диагностика<br /><br /> Ведение журнала служб HTTP<br /><br /> Монитор запросов<br /><br /> Производительность<br /><br /> Сжатие статического содержимого<br /><br /> Безопасность<br /><br /> Фильтрация запросов<br /><br /> Проверка подлинности Windows.|  
  
### Функции 
 В Windows Server 2012 и Windows Server 2012 R2 приведенные ниже компоненты можно установить с помощью **Диспетчера сервера**.  
  
||  
|-|  
|.NET Framework 3.5 (включая .NET 2.0 и 3.0)<br /><br /> Дополнительные службы .NET Framework 4.5 Advanced Services<br /><br /> ASP.NET 4.5<br /><br /> Службы WCF<br /><br /> Активация HTTP [Примечание: это обязательно.]<br /><br /> Совместное использование TCP-порта<br /><br /> Служба активации Windows<br /><br /> Модель процесса<br /><br /> Среда .NET<br /><br /> API-интерфейсы конфигурации|  
  
 Ниже приведен пример сценария PowerShell для добавления необходимых компонентов и ролей сервера. Необходимые роли и компоненты сервера зависят от среды.  
  
```powershell  
Install-WindowsFeature Web-Mgmt-Console, AS-NET-Framework, Web-Asp-Net, Web-Asp-Net45, Web-Default-Doc, Web-Dir-Browsing, Web-Http-Errors, Web-Static-Content, Web-Http-Logging, Web-Request-Monitor, Web-Stat-Compression, Web-Filtering, Web-Windows-Auth, NET-Framework-Core, WAS-Process-Model, WAS-NET-Environment, WAS-Config-APIs  
  
Install-WindowsFeature Web-App-Dev, NET-Framework-45-Features -IncludeAllSubFeature –Restart  
```  
  
 Дополнительные сведения о команде PowerShell см. в статье [Install-WindowsFeature](https://technet.microsoft.com/library/jj205467).  
  
### Учетные записи и разрешения  
  
|Тип|Описание|  
|----------|-----------------|  
|Учетная запись Windows|Выполнять вход на компьютер веб-сервера необходимо с учетной записью Windows, которая имеет разрешения на настройку ролей Windows, служб ролей и компонентов, а также на создание пулов приложений, веб-сайтов и веб-приложений в службах IIS на локальном компьютере и управление ими.|  
|Учетная запись службы|При создании веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] в программе [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]необходимо указать удостоверение для пула приложений, в котором оно выполняется. Эта учетная запись может отличаться от учетной записи службы, которая была указана при создании базы данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].<br /><br /> Данное удостоверение должно быть учетной записью пользователя домена, оно добавляется к роли базы данных mds_exec в базе данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] для доступа к ней. Дополнительные сведения см. в разделе [Имена входа, пользователи и роли базы данных (службы Master Data Services)](../../master-data-services/database-logins-users-and-roles-master-data-services.md). Данная учетная запись также добавляется в группу Windows [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], **MDS_ServiceAccounts**, которой предоставляется разрешение на доступ к временному каталогу компиляции **MDSTempDir** в файловой системе. Дополнительные сведения см. в статье [Разрешения для папок и файлов (службы Master Data Services)](../../master-data-services/folder-and-file-permissions-master-data-services.md).|  
  
## См. также:  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
 [Установка служб Master Data Services, а также ролей и компонентов IIS](../../sql-server/media/master-data-services.png)       
 [Создание веб-приложения мастера основных данных (службы Master Data Services)](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [Страница "Веб-конфигурация" (диспетчер конфигурации Master Data Services)](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
  