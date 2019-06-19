---
title: Настройка Integration Services (службы SSIS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- configuration files [Integration Services]
- service [Integration Services], configuring
- default configuration files
ms.assetid: 36d78393-a54c-44b0-8709-7f003f44c27f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 600858e3d7b2ea29a30541c559aa764b4085f7cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66060498"
---
# <a name="configuring-the-integration-services-service-ssis-service"></a>Настройка служб Integration Services (службы SSIS)
    
> [!IMPORTANT]  
>  В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] используют для определения параметров файл конфигурации. По умолчанию этот файл конфигурации называется MsDtsSrvr.ini.xml и файл расположен в папке %ProgramFiles%\Microsoft SQL Server\120\DTS\Binn.  
  
 Обычно не нужно делать какие-либо изменения в этом файле конфигурации или изменять расположение файла по умолчанию. Однако если пакеты хранятся в именованном или удаленном экземпляре компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]либо в нескольких экземплярах компонента [!INCLUDE[ssDE](../includes/ssde-md.md)], необходимо изменить файл конфигурации. Кроме того, если файл конфигурации переносится в расположение, отличное от расположения по умолчанию, необходимо изменить раздел реестра, указывающий расположение файла.  
  
## <a name="configuration-file-contents"></a>Содержимое файла конфигурации  
 При установке служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]процесс установки создает и устанавливает файл конфигурации для службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Этот файл конфигурации содержит следующие настройки.  
  
-   При остановки службы пакетам посылается команда остановки.  
  
-   Корневыми папками служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для отображения в обозревателе объектов среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] являются папки MSDB и файловой системы.  
  
-   Пакеты в файловой системе, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] служба управляет расположены в %ProgramFiles%\Microsoft SQL Server\120\DTS\Packages.  
  
 В этом файле конфигурации указывается, какая база данных msdb содержит пакеты, которыми будет управлять служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . По умолчанию служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] настроена для управления пакетами в базе данных msdb экземпляра компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , который установлен одновременно со службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Если экземпляр компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] не установлен в то же время, служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] будет настроена для управления пакетами базы данных msdb локального экземпляра по умолчанию компонента [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
### <a name="default-configuration-file-example"></a>Пример файла конфигурации по умолчанию  
 В следующем примере показан файл конфигурации по умолчанию, который задает следующие параметры.  
  
-   Выполнение пакетов прекращается, если останавливается служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
-   Корневыми папками для хранилища пакетов в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] являются MSDB и File System.  
  
-   Эта служба управляет пакетами, хранящимися в базе данных msdb локального экземпляра по умолчанию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Службы управляют пакетами, хранящимися в папке Packages файловой системы.  
  
 **Пример стандартного файла конфигурации**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>.</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file"></a>Изменение файла конфигурации  
 Можно изменить файл конфигурации, чтобы продолжить выполнение пакетов при остановке службы, отображать дополнительные корневые папки в обозревателе объектов или указать другую папку или дополнительные папки файловой системы, которые будут управляться службой [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Например, можно создать дополнительные корневые папки типа `SqlServerFolder`, чтобы управлять пакетами в базах данных msdb дополнительных экземпляров компонента [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
> [!NOTE]  
>  Некоторые символы в именах папок являются недопустимыми. Допустимые знаки в именах папок определяются классом [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] **System.IO.Path** и полем **GetInvalidFilenameChars** . Поле **GetInvalidFilenameChars** содержит специфический для платформы набор знаков, которые не могут быть использованы в аргументах, содержащих строки пути и передаваемых элементам класса **Path** . Набор недопустимых символов меняется в зависимости от файловой системы. Обычно недопустимые символы включают кавычки ("), знак «меньше» (<) и вертикальную черту (|).  
  
 Однако чтобы управлять пакетами, хранящимися в именованном или удаленном экземпляре компонента [!INCLUDE[ssDE](../includes/ssde-md.md)], необходимо изменить файл конфигурации. Если не обновить файл конфигурации, в среде **нельзя будет использовать** обозреватель объектов [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , чтобы просмотреть пакеты, хранящиеся в базе данных msdb на именованном или удаленном экземпляре. При попытке использовать **обозреватель объектов** для просмотра этих пакетов появляется следующее сообщение об ошибке.  
  
 `Failed to retrieve data for this request. (Microsoft.SqlServer.SmoEnum)`  
  
 `The SQL Server specified in Integration Services service configuration is not present or is not available. This might occur when there is no default instance of SQL Server on the computer. For more information, see the topic "Configuring the Integration Services Service" in SQL Server 2008 Books Online.`  
  
 `Login Timeout Expired`  
  
 `An error has occurred while establishing a connection to the server. When connecting to SQL Server 2008, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.`  
  
 `Named Pipes Provider: Could not open a connection to SQL Server [2]. (MsDtsSvr).`  
  
 Чтобы изменить файл конфигурации для службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , используется текстовый редактор.  
  
> [!IMPORTANT]  
>  После изменения файла конфигурации службы необходимо перезапустить службы, чтобы они использовали обновленную конфигурацию.  
  
### <a name="modified-configuration-file-example"></a>Пример измененного файла конфигурации  
 В следующем примере показан модифицированный файл конфигурации для службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Этот файл предназначен для именованного экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , называемого `InstanceName` на сервере с именем `ServerName`.  
  
 **Пример модифицированного файла конфигурации для именованного экземпляра SQL Server**  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<DtsServiceConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <StopExecutingPackagesOnShutdown>true</StopExecutingPackagesOnShutdown>  
  <TopLevelFolders>  
    <Folder xsi:type="SqlServerFolder">  
      <Name>MSDB</Name>  
      <ServerName>ServerName\InstanceName</ServerName>  
    </Folder>  
    <Folder xsi:type="FileSystemFolder">  
      <Name>File System</Name>  
      <StorePath>..\Packages</StorePath>  
    </Folder>  
  </TopLevelFolders>    
</DtsServiceConfiguration>  
```  
  
## <a name="modification-of-the-configuration-file-location"></a>Изменение расположения файла конфигурации  
Раздел реестра **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\ServiceConfigFile** указывает расположение и имя для конфигурации файла, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] использует служба. Значение по умолчанию раздела реестра — **C:\Program Files\Microsoft SQL Server\120\DTS\Binn\MsDtsSrvr.ini.xml**. Можно изменить значение этого раздела реестра, чтобы использовать другое имя и местонахождение файла конфигурации. Обратите внимание, что номер версии в пути (120 для SQL Server [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)]) будет зависеть от версии SQL Server. 
  
  
> [!CAUTION]  
>  Неправильное изменение реестра может приводить к серьезным проблемам, вплоть до необходимости переустановки операционной системы. [!INCLUDE[msCoName](../includes/msconame-md.md)] не гарантирует возможность разрешения проблем, возникших в результате неправильного изменения реестра. Перед изменением реестра создайте резервную копию всех необходимых данных. Дополнительные сведения о том, как выполнять создание резервной копии, восстановление и изменение системного реестра, см. в [!INCLUDE[msCoName](../includes/msconame-md.md)] статье базы знаний [Описание системного реестра Microsoft Windows](https://support.microsoft.com/kb/256986).  
  
 Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] загружают файл конфигурации при запуске. Все изменения записей реестра требуют перезапуска службы.  
  
  
