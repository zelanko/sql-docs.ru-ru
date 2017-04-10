---
title: "Установка SQL Server 2016 на Server Core | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dd294cc-5b69-4d0c-9005-3e307b75678b
caps.latest.revision: 43
ms.author: "mikeray"
manager: "jhubbard"
---
# Установка SQL Server 2016 на Server Core
  Можно установить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поверх установленной Server Core ОС [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)]. В этом разделе приводятся подробные сведения, относящиеся к установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на Windows Server Core.  
  
 Вариант установки Server Core для операционной системы [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] или [!INCLUDE[win8srv](../../includes/win8srv-md.md)] предусматривает наличие среды, минимально необходимой для запуска конкретных ролей сервера. Это дает возможность снизить требования к обслуживанию и управлению и уменьшить уязвимость для атак со стороны этих ролей сервера. Дополнительные сведения о реализации Server Core в операционной системе [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] см. в разделе [Server Core для Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=202439) (http://go.microsoft.com/fwlink/?LinkId=202439). Дополнительные сведения о реализации Server Core в операционной системе [!INCLUDE[win8srv](../../includes/win8srv-md.md)] см. в разделе [Server Core для Windows Server 2012](http://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (http://msdn.microsoft.com/library/hh846323(VS.85).aspx).  
  
## <a name="prerequisites"></a>Предварительные требования  
  
|Требование|Как установить|  
|-----------------|--------------------|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 2.0 с пакетом обновления 2 (SP2)|Входит в программу установки Server Core [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1) и [!INCLUDE[win8srv](../../includes/win8srv-md.md)]. Если платформа не разрешена, то программа установки включает ее по умолчанию.<br /><br /> Невозможно параллельно запустить на данном компьютере версии 2.0, 3.0 и 3.5. При установке платформы .NET Framework 3.5 с пакетом обновления 1 (SP1) вы получаете уровни 2.0 и 3.0 автоматически.|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 3.5 с пакетом обновления 1 (SP1) Full Profile|Входит в программу установки Server Core [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1). Если платформа не разрешена, то программа установки включает ее по умолчанию.<br /><br /> На компьютере, работающем под управлением серверной ОС Windows, необходимо загрузить и установить платформу .NET Framework 3.5 с пакетом обновления 1 (SP1) перед началом установки, чтобы установить компоненты, зависимые от .NET Framework 3.5 с пакетом обновления 1 (SP1).<br /><br /> Дополнительные сведения о рекомендациях и указания о том, как получить и включить платформу .NET Framework 3.5 в [!INCLUDE[win8srv](../../includes/win8srv-md.md)], см. в разделе [Требования к развертыванию платформы Microsoft .NET Framework 3.5](http://msdn.microsoft.com/library/windows/hardware/hh975396) (http://msdn.microsoft.com/library/windows/hardware/hh975396).|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile|Для всех выпусков [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], кроме [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], программа установки устанавливает платформу [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core Profile как обязательное ПО.|  
|Установщик Windows 4.5|Поставляется с установкой Server Core с [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1) и [!INCLUDE[win8srv](../../includes/win8srv-md.md)].|  
|Windows PowerShell|Поставляется с установкой Server Core с [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1) и [!INCLUDE[win8srv](../../includes/win8srv-md.md)].|  
  
##  <a name="a-namebksupportedfeaturesa-supported-features"></a> Поддерживаемые функции  
 В следующей таблице можно найти компоненты, которые поддерживаются в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в установке Server Core ОС [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1) и [!INCLUDE[win8srv](../../includes/win8srv-md.md)].  
  
|Компонент|Поддерживается|Дополнительные сведения|  
|-------------|---------------|----------------------------|  
|Службы [!INCLUDE[ssDE](../../includes/ssde-md.md)]|Да||  
|Репликация [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Да||  
|Полнотекстовый поиск|Да||  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Да||  
|[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]|Да||  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Нет||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Tools (SSDT)|Нет||  
|Средства связи клиентских средств|Да||  
|Сервер служб Integration Services|Да|Дополнительные сведения о новом сервере служб Integration Services и его компонентах в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] см. в разделе [Сервер служб Integration Services (SSIS)](https://msdn.microsoft.com/library/bb522534.aspx).|  
|Обратная совместимость клиентских средств|Нет||  
|Пакет SDK клиентских средств|Нет||  
|Электронная документация по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Нет||  
|Основные средства управления|Только удаленные|Установка этих компонентов на Server Core не поддерживается. Эти компоненты могут быть установлены на другом сервере, отличном от [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, и подключены к службам [!INCLUDE[ssDE](../../includes/ssde-md.md)], установленным в Server Core.|  
|Полные средства управления|Только удаленные|Установка этих компонентов на Server Core не поддерживается. Эти компоненты могут быть установлены на другом сервере, отличном от [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, и подключены к службам [!INCLUDE[ssDE](../../includes/ssde-md.md)], установленным в Server Core.|  
|Контроллер распределенного воспроизведения|Нет||  
|Клиент распределенного воспроизведения|Только удаленные|Установка этих компонентов на Server Core не поддерживается. Эти компоненты могут быть установлены на другом сервере, отличном от [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, и подключены к службам [!INCLUDE[ssDE](../../includes/ssde-md.md)], установленным в Server Core.|  
|Пакет SDK для подключения клиентов SQL|Да||  
|Microsoft Sync Framework|Да|Платформа Microsoft Sync Framework не входит в установочный пакет [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Вы можете скачать соответствующую версию Sync Framework в [Центре загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=221788) (http://go.microsoft.com/fwlink/?LinkId=221788) и установить ее на компьютер, где работает установка Server Core [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)].|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|Нет||  
|[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]|Нет||  
  
## <a name="supported-scenario-matrix"></a>Матрица поддерживаемых сценариев  
 В следующей таблице показана матрица поддерживаемых сценариев для установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на экземпляре Server Core [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1) и [!INCLUDE[win8srv](../../includes/win8srv-md.md)].  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выпуски|Все 64-разрядные версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] *|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], язык|Все языки|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], язык в языке ОС-локали (сочетание)|ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для JPN (японский) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для GER (немецкий) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для CHS (китайский — Китай) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для ARA (арабский (SA)) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для THA (тайский) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для TRK (турецкий) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для pt-PT (португальский, Португалия) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для ENG (английский) Windows|  
|Выпуск Windows|64-разрядная версия [!INCLUDE[win8srv](../../includes/win8srv-md.md)] x64 Datacenter<br /><br /> 64-разрядная версия [!INCLUDE[win8srv](../../includes/win8srv-md.md)] x64 Standard<br /><br /> 64-разрядная версия [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] x64 Data Center Server Core Edition с пакетом обновления 1 (SP1)<br /><br /> 64-разрядная версия [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] x64 Enterprise Server Core с пакетом обновления 1 (SP1)<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]Windows Server Standard Server Core с пакетом обновления 1 (SP1) для 64-разрядных систем с архитектурой x64<br /><br /> 64-разрядная версия [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] x64 Web Server Core с пакетом обновления 1 (SP1)|  
  
 * Установка 32-разрядных выпусков [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживается в Server Core.  
  
## <a name="upgrading"></a>Обновление  
 В установках Server Core поддерживается обновление с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
## <a name="installation"></a>Установка  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает установку с помощью мастера установки в операционной системе Server Core. При установке на Server Core программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает полный тихий режим без вывода сообщений с использованием параметра /Q или простой режим без вывода сообщений с использованием параметра /QS. Дополнительные сведения см. в статье [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] нельзя установить параллельно с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере с [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core.  
  
 Независимо от метода установки, необходимо подтвердить свое согласие с условиями лицензии на использование пакета программ как физического лица или от имени организации, если на используемое программное обеспечение не распространяется отдельное соглашение [!INCLUDE[msCoName](../../includes/msconame-md.md)], такое как соглашение о корпоративном лицензировании Майкрософт или отдельное соглашение с независимым поставщиком программного обеспечения или изготовителем оборудования (OEM).  
  
 Условия лицензионного соглашения отображаются для ознакомления и принятия в пользовательском интерфейсе программы установки. Автоматические установки (с использованием параметров /Q или /QS) должны включать параметр /IACCEPTSQLSERVERLICENSETERMS. Ознакомиться с условиями лицензии можно на странице [Условия лицензионного соглашения о программном обеспечении Майкрософт](http://go.microsoft.com/fwlink/?LinkId=148209).  
  
> [!NOTE]  
>  В зависимости от способа получения ПО (например, по [!INCLUDE[msCoName](../../includes/msconame-md.md)]), на его использование могут распространяться дополнительные условия.  
  
 Для установки отдельных компонентов используйте параметр /FEATURES и укажите значения родительского компонента или компонентов. Дополнительные сведения о параметрах компонентов и их использовании см. в следующих подразделах.  
  
### <a name="feature-parameters"></a>Параметры компонентов  
  
|Параметр компонента|Описание|  
|-----------------------|-----------------|  
|SQLENGINE|Устанавливает только компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|REPLICATION|Устанавливает компонент репликации вместе с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|FULLTEXT|Устанавливает компонент FullText вместе с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|AS|Устанавливает все компоненты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|IS|Устанавливает все компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|  
|CONN|Устанавливает компоненты подключения к данным.| 
|ADVANCEDANALYTICS |Устанавливает службы R Services; требуется ядро СУБД. Для автоматической установки требуется параметр /IACCEPTROPENLICENSETERMS.  |


 В следующих примерах показано использование параметров компонентов.  
  
|Параметр и значения|Описание|  
|--------------------------|-----------------|  
|/FEATURES=SQLEngine|Устанавливает только компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|/FEATURES=SQLEngine, FullText|Устанавливает компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] с компонентом Full-Text Search.|  
|/FEATURES=SQLEngine, Conn|Устанавливает компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] и компоненты подключения к данным.|  
|/FEATURES=SQLEngine, AS, IS, Conn|Устанавливает компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и компоненты подключения к данным.|  
|/FEATURES=SQLENGINE,ADVANCEDANALYTICS /IACCEPTROPENLICENSETERMS |Устанавливает [!INCLUDE[ssDE](../../includes/ssde-md.md)] и [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)].|  

  
### <a name="installation-options"></a>Варианты установки  
 Программа установки поддерживает следующие варианты установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в операционной системе Server Core.  
  
1.  **Установка из командной строки**  
  
     Чтобы установить конкретные компоненты с помощью командной строки, необходимо использовать параметр /FEATURES и указать родительский компонент или конкретные компоненты. Ниже приведен пример указания параметров в командной строке.  
  
    ```  
    Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /TCPENABLED=1 /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
2.  **Установка с помощью файла конфигурации**  
  
     Программа установки поддерживает использование файлов конфигурации только через командную строку. Файл конфигурации — это текстовый файл, содержащий параметры (пара «имя-значение») и комментарии с описанием. Файл конфигурации, который указывается в командной строке, должен иметь расширение INI. Ниже приведены примеры файла ConfigurationFile.ini.  
  
    -   Установка [!INCLUDE[ssDE](../../includes/ssde-md.md)]. В следующем примере показано, как установить новый автономный экземпляр, который включает компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine, and Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Accept the License agreement to continue with Installation  
  
        IAcceptSQLServerLicenseTerms="True"  
  
        ```  
  
    -   Установка компонентов подключения к данным. Следующий пример показывает, как установить компоненты подключения к данным:  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=Conn  
  
        ; Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True  
  
        ```  
  
    -   Установка всех поддерживаемых компонентов  
  
         . Следующий пример показывает, как установить все поддерживаемые компоненты [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в Server Core:  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE,FullText,Replication,AS,IS,Conn  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine (SQL), or Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; The name of the account that the Analysis Services service runs under.   
  
        ASSVCACCOUNT= "NT Service\MSSQLServerOLAPService"  
  
        ; Specifies the list of administrator accounts that need to be provisioned.   
  
        ASSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Specifies the server mode of the Analysis Services instance. Valid values are MULTIDIMENSIONAL, POWERPIVOT or TABULAR. ASSERVERMODE is case-sensitive. All values must be expressed in upper case.   
  
        ASSERVERMODE="MULTIDIMENSIONAL"  
  
        ; Optional value, which specifies the state of the TCP protocol for the ssNoVersion service. Supported values are: 0 to disable the TCP protocol, and 1 to enable the TCP protocol.  
  
        TCPENABLED=1  
  
        ;Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True"  
        ```  
  
     Далее показан процесс запуска установки с использованием пользовательского или стандартного файла конфигурации.  
  
    -   Запуск установки с использованием пользовательского файла конфигурации.  
  
         Указание файла конфигурации в командной строке:  
  
        ```  
        Setup.exe /QS /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
         Указание паролей в командной строке, а не в файле конфигурации:  
  
        ```  
        Setup.exe /QS /SQLSVCPASSWORD="************" /ASSVCPASSWORD="************"  /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
    -   Запуск установки с использованием DefaultSetup.ini.  
  
         Если файл DefaultSetup.ini находится в папках \x86 и \x64 в корневой папке исходного носителя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], откройте этот файл и добавьте в него параметр *Features*.  
  
         Если файл DefaultSetup.ini не существует, создайте его и скопируйте в папки \x86 и \x64 корневой папки исходного носителя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="configuring-remote-access-of-includessnoversiontokenssnoversionmdmd-running-on-server-core"></a>Настройка удаленного доступа для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при работе на Server Core  
 Чтобы настроить удаленный доступ к экземпляру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], который запускается в установке Server Core ОС [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)], выполните действия, описанные ниже.  
  
### <a name="enable-remote-connections-on-the-instance-of-includessnoversiontokenssnoversionmdmd"></a>Включение удаленных подключений на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Чтобы разрешить удаленные соединения, выполните следующие инструкции для экземпляра Server Core в локальной программе SQLCMD.exe.  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-includessnoversiontokenssnoversionmdmd-browser-service"></a>Включите и запустите службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 По умолчанию эта служба отключена.  Если она отключена на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , работающем на Server Core, то для ее включения выполните следующую команду из командной строки:  
  
 `sc config SQLBROWSER start= auto`  
  
 После включения службы выполните следующую команду из командной строки, чтобы запустить службу:  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a>Создание исключений в брандмауэре Windows  
 Чтобы создать исключения в брандмауэре Windows для доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните действия, описанные в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
### <a name="enable-tcpip-on-the-instance-of-includessnoversiontokenssnoversionmdmd"></a>Включите поддержку TCP/IP на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Протокол TCP/IP для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Server Core можно включить через Windows PowerShell. Выполните следующие действия.  
  
1.  На компьютере, где запущена ОС [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, запустите диспетчер задач.  
  
2.  На вкладке **Приложения** нажмите **Создать задачу**.  
  
3.  В диалоговом окне **Создание новой задачи** введите **sqlps.exe** в поле **Открыть** и нажмите кнопку **ОК**. Откроется окно **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell**.  
  
4.  В окне **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** выполните следующий скрипт, чтобы включить протокол TCP/IP:  
  
```  
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = new-object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
## <a name="uninstallation"></a>Удаление  
 После входа на компьютер, где работает [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core с пакетом обновления 1 (SP1) или [!INCLUDE[win8srv](../../includes/win8srv-md.md)], вы получите доступ к ограниченной среде с командной строкой администратора. В этой командной строке можно запустить процесс удаления экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Чтобы удалить экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], запустите удаление из командной строки — либо в полностью тихом режиме (параметр /Q), либо в простом тихом режиме (параметр /QS). Если указан параметр /QS, то ход выполнения будет отображаться в пользовательском интерфейсе, но не потребует ввода. Параметр /Q запускает тихий режим без пользовательского интерфейса.  
  
 Удаление существующего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
Setup.exe /Q /Action=Uninstall /FEATURES=SQLEngine,AS,IS /INSTANCENAME=MSSQLSERVER  
```  
  
 Чтобы удалить именованный экземпляр, укажите его имя вместо имени MSSQLSERVER, указанного в предыдущем примере.  
  
> [!WARNING]  
>  Если окно командной строки было случайно закрыто, то его можно открыть снова, выполнив следующие действия.  
>   
>  1.  Нажмите CTRL+SHIFT+ESC, чтобы отобразить диспетчер задач.  
> 2.  На вкладке **Приложения** нажмите **Создать задачу**.  
> 3.  В диалоговом окне **Создание новой задачи** введите **cmd** в поле **Открыть[!INCLUDE[clickOK](../../includes/clickok-md.md)], а затем **.  
  
## <a name="see-also"></a>См. также:  
 [Установка SQL Server 2016, с помощью файла конфигурации](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)   
 [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [Возможности, поддерживаемые различными выпусками SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [Server Core Installation Option Getting Started Guide (Руководство по использованию параметров установки Server Core)](http://go.microsoft.com/fwlink/?LinkId=221422)   
 [Configuring a Server Core installation: Overview (Обзор настройки установки Server Core)](http://go.microsoft.com/fwlink/?LinkId=221423)   
 [Командлеты отказоустойчивого кластера в Windows PowerShell по выполняемым задачам](http://go.microsoft.com/fwlink/?LinkId=221419)   
 [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters (Сопоставление команд Cluster.exe с командлетами Windows PowerShell для отказоустойчивых кластеров)](http://go.microsoft.com/fwlink/?LinkId=221421)  
  
  