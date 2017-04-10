---
title: "PowerShell scripting in Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
caps.latest.revision: 44
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 44
---
# PowerShell scripting in Analysis Services
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] включает в себя компоненты PowerShell для переходов, администрирования и подачи запросов на сервер служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], в табличные и многомерные объекты:  
  
-   Поставщик **SQLAS**, используемый для навигации по иерархии объектов, доступен при наличии локального экземпляра служб Analysis Services (режим сервера значения не имеет).  
  
-   Модуль **SQLASCMDLETS** предоставляет командлеты для конкретных задач, таких как резервное копирование, восстановление, обработка, а также [командлет Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md) общего назначения, принимающий инструкции ASSL/XMLA или языка скриптов табличной модели (TMSL) в виде входного файла запроса или скрипта.  
  
 Эти компоненты реализуют подмножество интерфейса администрирования объекта управления для служб Analysis Services (пространство имен [Microsoft.AnalysisServices](http://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx)), предоставляя командлеты для создания объектов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и управления ими.  Оба компонента являются расширениями корневого модуля **SQLPS** для SQL Server. Чтобы использовать компоненты [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell, сначала импортируйте **SQLPS**. Синтаксис и примеры для всех командлетов см. в разделе [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md).  Пример использования типов объектов AMO в PowerShell для создания табличной базы данных см. в разделе [AMO PowerShell Example](../../analysis-services/powershell/amo-powershell-example.md).  
  
##  <a name="bkmk_prereq"></a> Этап 1. Установка компонентов PowerShell  
 Для получения компонентов PowerShell рекомендуется установить среду SQL Server Management Studio (SSMS). Такой подход обеспечивает получение модулей PowerShell для SQL Server и поставщика данных для управления службами Analysis Services (AMO). Среда SSMS, помимо прочего, предоставляет средство для создания инструкций на XMLA и TMSL для использования в скриптах PowerShell.  
  
 Рекомендуется установить локальный экземпляр служб Analysis Services. Локальный экземпляр позволяет осуществлять переходы по иерархии объектов с помощью поставщика **SQLAS** , даже если вы никогда не использовали его для размещения базы данных.  
  
1.  Чтобы получить последнюю версию среды Management Studio, перейдите на страницу  [Загрузка SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx) . Последний выпуск среды Management Studio включает в себя обновленные объекты AMO, поддерживающие определения табличных объектов метаданных для табличных моделей, созданных на уровне совместимости 1200.  
  
2.  После установки среды Management Studio откройте окно PowerShell. Это не обязательно должно быть окно администратора.  
  
3.  Введите `Get-Module -ListAvailable`, чтобы убедиться, что модули **SQLPS** и **SQLASCMDLETS** отображаются в списке.  
  
     Вы не увидите **SQLAS**, если, помимо прочего, не будет установлен локальный экземпляр служб Analysis Services (многомерный или табличный режим).  
  
4.  Введите `Get-Command -Module sqlascmdlets` для получения списка командлетов, используемых для администрирования служб Analysis Services.  
  
     Командлет**SQLASCMDLETS** доступен даже при отсутствии поставщика **SQLAS** .  
  
    -   [Командлет Add-RoleMember](../../analysis-services/powershell/add-rolemember-cmdlet.md)  
  
    -   [Командлет Backup-ASDatabase](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)  
  
    -   [Командлет Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md) **-inputfile**  
  
    -   [Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)  
  
    -   [Командлет Invoke-ProcessCube](../../analysis-services/powershell/invoke-processcube-cmdlet.md)  
  
    -   [Командлет Invoke-ProcessDimension](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)  
  
    -   [Командлет Invoke-PolicyEvaluation](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)  
  
    -   [Командлет Invoke-ProcessTable](../../analysis-services/powershell/invoke-processtable-cmdlet.md)  
  
    -   [Командлет Merge-Partition](../../analysis-services/powershell/merge-partition-cmdlet.md)  
  
    -   [Командлет New-RestoreFolder](../../analysis-services/powershell/new-restorefolder-cmdlet.md)  
  
    -   [Командлет New-RestoreLocation](../../analysis-services/powershell/new-restorelocation-cmdlet.md)  
  
    -   [Командлет Remove-RoleMember](../../analysis-services/powershell/remove-rolemember-cmdlet.md)  
  
    -   [Командлет Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)  
  
> [!NOTE]  
>  В последних версиях операционных систем Windows оболочка Windows PowerShell устанавливается по умолчанию. Рекомендуется версия 4.0 или более поздняя.  
  
## Этап 2. Загрузка компонентов для запуска интерактивного сеанса  
 После установки компонентов их загрузка означает начало интерактивного сеанса.  
  
1.  Введите команду `Import-Module sqlps -DisableNameChecking`.  
  
     Будут загружены компоненты SQL Server PowerShell, включая те, которые нужны для служб Analysis Services, и подавлены предупреждения о недопустимых именах команд.  
  
2.  Введите `sqlserver:`  
  
     Приглашение должно измениться на **PS SQLSERVER:\\>**.  
  
3.  Если службы Analysis Services установлены локально, можно перемещаться по иерархии объектов. Введите `cd sqlas`, чтобы открыть поставщик **SQLAS**.  
  
4.  Введите `dir` для получения списка экземпляров служб Analysis Services. Поставщик не различает табличные и многомерные экземпляры.  
  
## Permissions  
 Интерактивный сеанс PowerShell выполняется с удостоверением безопасности того пользователя, который запускает его. Для большинства задач требуется, чтобы пользователь, инициирующий сеанс, был, помимо прочего, администратором сервера служб Analysis Services.  
  
 Запланированные задания PowerShell следует рассматривать как автоматические операции. Чаще всего требуется, чтобы учетная запись, с использованием которой выполняется планировщик, например служба агента SQL Server, была учетной записью администратора служб Analysis Services (в зависимости от задач).  
  
 Для папок локальных данных, таких как каталоги резервного копирования и каталоги данных, заданных по умолчанию, уже определены разрешения файловой системы, позволяющие локальному экземпляру производить чтение и запись в этих расположениях.  
  
 При выполнении операций удаленного администрирования, особенно в случаях, когда они выполняются с клиентских компьютеров, на которых не установлены службы Analysis Services, требуется, чтобы удаленный экземпляр сервера Analysis Services, выполняющий операции, имел разрешения файловой системы на чтение файлов во время восстановления или на запись во время резервного копирования файлов.  
  
## Входные файлы скрипта: ASSL/XMLA или TMSL  
 Если вы используете **invoke-ascmd** для выполнения скрипта, при создании скрипта необходимо учитывать режим сервера, тип базы данных и уровень совместимости.  
  
-   Многомерные и табличные базы данных на уровнях совместимости 1050–1103 отвечают на скрипты, написанные на XML (с использованием расширений языка ASSL, касающихся определений объектов служб Analysis Services).  
  
-   Табличные базы данных в SQL Server 2016 (уровень совместимости 1200) отвечают на скрипты TMSL.  
  
 Если вы работаете с разными версиями табличных моделей на одном и том же экземпляре сервера SQL Server 2016, не забывайте использовать соответствующий скрипт.  
  
> [!NOTE]  
>  Скрипты можно создавать в среде SQL Server Management Studio, а затем изменять при необходимости. Табличные базы данных на уровне совместимости 1200 настроены для работы со скриптами на TMSL. Все остальные настроены для работы со скриптами на XMLA и ASSL. Экземпляр SQL Server 2016 в табличном режиме поддерживает оба языка скриптов.  
  
## Локальное и удаленное администрирование  
 Осуществлять локальное администрирование служб Analysis Services с помощью скриптов и команд PowerShell проще. Это обусловлено двумя причинами.  
  
-   Для переходов по иерархии объектов используется поставщик **SQLAS** .  
  
-   Разрешения, позволяющие службам Analysis Services выполнять чтение из папок данных, заданных по умолчанию, например для задач резервного копирования и восстановления, уже имеются. Это справедливо при условии, что вы используете эти папки как расположение базы данных, а для операций используется экземпляр локального сервера.  
  
 Управление удаленным экземпляром требует дополнительной настройки. При выполнении следующих действий предполагается, что среда Management Studio установлена, но экземпляр службы находится на удаленном компьютере. Необходимо иметь права администратора на сервере служб Analysis Services.  
  
 Поскольку службы Analysis Services являются удаленными, для локальных переходов по иерархии объектов нет поставщика **SQLAS** . При восстановлении файлов из локальной папки, а не из экземпляра служб Analysis Services необходимо создавать общие папки и предоставлять серверу доступ на чтение файлов.  
  
1.  Откройте окно администратора PowerShell.  
  
2.  Введите `Set-ExecutionPolicy RemoteUnsigned`  
  
3.  Используя проводник, убедитесь, что все папки, хранящие файлы данных, объявлены как общие и что экземпляру служб Analysis Services предоставлены разрешения на чтение их содержимого.  
  
##  <a name="bkmk_vers"></a> Поддерживаемые версии и режимы служб Analysis Services  
 В следующей таблице приведены данные по доступности Analysis Services PowerShell в различных контекстах.  
  
|Контекст|Доступность функций PowerShell|  
|-------------|-------------------------------------|  
|Многомерные экземпляры и базы данных|Поддерживается локальное и удаленное администрирование.<br /><br /> Для слияния секций необходимо локальное соединение.|  
|Табличные экземпляры и базы данных|Поддерживается локальное и удаленное администрирование на всех уровнях совместимости.<br /><br /> Командлеты SQLAS для табличных моделей на уровне совместимости 1200 с использованием языка скриптов табличных моделей (TMSL) в формате JSON вместо XMLA.|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|Ограниченная поддержка. Для просмотра сведений об экземпляре и базе данных можно использовать соединения HTTP и поставщик SQLAS.<br /><br /> Однако использование командлетов не поддерживается. Надстройку PowerShell для служб Analysis Services нельзя использовать для резервного копирования и восстановления хранящихся в памяти баз данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], а также для добавления и удаления ролей, обработки данных или запуска произвольных скриптов XMLA.<br /><br /> В целях настройки в [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint имеется встроенная поддержка PowerShell, реализуемая отдельно. Дополнительные сведения см. в разделе [Справочник по PowerShell для Power Pivot для SharePoint](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md).|  
|Собственные соединения с локальными кубами<br /><br /> “Data Source=c:\backup\test.cub”|Не поддерживается.|  
|Соединения HTTP с файлами соединений семантических моделей бизнес-аналитики (BISM-файлами) в SharePoint<br /><br /> “Data Source=http://server/shared_docs/name.bism”|Не поддерживается.|  
|Встроенные соединения с базами данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> “Data Source=$Embedded$”|Не поддерживается.|  
|Контекст локального сервера в хранимых процедурах служб Analysis Services<br /><br /> “Data Source=*”|Не поддерживается.|  
  
## Примеры выполнения задач администрирования сервера с помощью PowerShell  
 **Просмотр свойств сервера**  
  
 Свойства сервера предоставляются несколькими способами.  Если вы знакомы со свойствами, предоставляемыми в файле msmdsrv. ini или на страницах свойств среды Management Studio, вы увидите в приведенных ниже примерах, что свойства на самом деле возвращаются с разных объектов.  
  
 Этот скрипт загружает объект AMO Server. Если требуется полное доменное имя свойства, можно запустить этот скрипт для получения списка.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.connect("server-name\instance-name")  
$as.serverproperties  
  
```  
  
 Этот скрипт возвращает свойства и методы на уровне экземпляра. Из этого списка можно считывать такие значения, как **ServerMode**, **Version**, **ProductName**и **ProductLevel**.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as | get-member  
  
```  
  
 **Получение режима сервера**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.ServerMode  
```  
  
 **Получение уровня совместимости по умолчанию**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.DefaultCompatibilityLevel  
```  
  
 **Получение списка баз данных**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.databases  
```  
  
 **Получение номера порта**  
  
 Этот скрипт создает объект для именованного экземпляра, объявляет порт, настраивает порт, обновляет экземпляр сервера, отключает объект и перезапускает службу. В качестве проверки можно открыть новое соединение и получить порт.  
  
 Кроме того, проверить порт можно в файле msmdsrv.ini или на главной странице свойств сервера в среде Management Studio.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.connect("server-name\instance-name")  
$port = $as.serverproperties['Port']  
$port | select *  
$port.Value = [int]55555  
$as.Update()  
$as.Disconnect()  
restart-service 'MSOLAP$TABULAR'  
$as.connect("server-name\instance-name")  
$port | select *  
  
```  
  
## См. также  
 [Предоставление прав администратора сервера для экземпляра служб Analysis Services](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Справочник по языку TMSL (Tabular Model Scripting Language)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Установка компонентов SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)   
 [Управление табличными моделями с помощью PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)   
 [Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md)  
  
  