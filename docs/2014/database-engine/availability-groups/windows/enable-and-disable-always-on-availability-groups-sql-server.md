---
title: Включение и отключение группы доступности AlwaysOn (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 585f1d86d328b7c5027241310108d102b56ca327
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936855"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a>Включение и отключение групп доступности AlwaysOn (SQL Server)
  Включение [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] является предварительным условием для того, чтобы экземпляр сервера мог использовать группы доступности. Перед тем как создавать и настраивать любую группу доступности, следует включить компонент [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] на каждом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , где будет размещаться реплика доступности для одной или нескольких групп доступности.  
  
> [!IMPORTANT]  
>  При удалении и повторном создании кластера WSFC необходимо отключить и повторно включить функцию [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в каждом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , который обеспечил размещение реплики доступности в исходном кластере WSFC.  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Инструкции:**  
  
    -   [Определите, включены ли группы доступности AlwaysOn](#IsEnabled)  
  
    -   [Включение групп доступности AlwaysOn](#EnableAOAG)  
  
    -   [Отключите группы доступности AlwaysOn](#DisableAOAG)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites-for-enabling-alwayson-availability-groups"></a><a name="Prerequisites"></a>Необходимые условия для включения группы доступности AlwaysOn  
  
-   Экземпляр сервера должен находиться на узле отказоустойчивой кластеризации Windows Server (WSFC).  
  
-   Экземпляр сервера должен работать на выпуске SQL Server, который поддерживает [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Дополнительные сведения см. [в разделе функции, поддерживаемые различными Выпусками SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   Включайте группы доступности AlwaysOn только на одном экземпляре сервера единовременно. После включения групп доступности AlwaysOn подождите, пока служба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не перезапустится, и только после этого включайте следующий экземпляр.  
  
 Дополнительные сведения о дополнительных предварительных требованиях для создания и настройки групп доступности см. в разделе [Предварительные требования, ограничения и рекомендации для группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Когда группы доступности AlwaysOn включены на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], экземпляр сервера получает полный контроль над кластером WSFC.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется членство в группе **Администратор** на локальном компьютере и полный контроль над кластером WSFC. При включении функции AlwaysOn при помощи консоли PowerShell, откройте окно командной строки, используя команду **Запуск от имени администратора** .  
  
 Требуются разрешения Active Directory на создание объектов и управление объектами.  
  
##  <a name="determine-whether-alwayson-availability-groups-is-enabled"></a><a name="IsEnabled"></a>Определение того, включена ли группы доступности AlwaysOn  
  
-   [Среда SQL Server Management Studio](#SSMS1Procedure)  
  
-   [Transact-SQL](#Tsql1Procedure)  
  
-   [PowerShell](#PowerShell1Procedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMS1Procedure"></a> Использование среды SQL Server Management Studio  
 **Определение того, включены ли группы доступности AlwaysOn**  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр сервера и выберите команду **Свойства**.  
  
2.  В диалоговом окне **Свойства сервера** перейдите на страницу **Общие** . Свойство **HADR включен** имеет одно из следующих значений:  
  
    -   **True**, если группы доступности AlwaysOn включены  
  
    -   **False**, если группы доступности AlwaysOn отключены  
  
###  <a name="using-transact-sql"></a><a name="Tsql1Procedure"></a> Использование Transact-SQL  
 **Определение того, включены ли группы доступности AlwaysOn**  
  
1.  Используйте следующую инструкцию [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) :  
  
    ```sql
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     Значение свойства сервера `IsHadrEnabled` указывает, может ли экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] входить в группы доступности AlwaysOn следующим образом:  
  
    -   Если значение свойства `IsHadrEnabled` = 1, это означает группы доступности AlwaysOn включены.  
  
    -   Если значение свойства `IsHadrEnabled` = 0, это означает, что группы доступности AlwaysOn отключены.  
  
    > [!NOTE]  
    >  Дополнительные сведения о `IsHadrEnabled` свойстве сервера см. в разделе [SERVERPROPERTY &#40;TRANSACT-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql).  
  
###  <a name="using-powershell"></a><a name="PowerShell1Procedure"></a> Использование PowerShell  
 **Определение того, включены ли группы доступности AlwaysOn**  
  
1.  Задайте для параметра Default ( `cd` ) экземпляр сервера (например, `\SQL\NODE1\DEFAULT` ), для которого необходимо определить [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , включен ли параметр.  
  
2.  Введите следующую команду PowerShell `Get-Item`:  
  
    ```powershell
    Get-Item . | Select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="enable-alwayson-availability-groups"></a><a name="EnableAOAG"></a>Включить группы доступности AlwaysOn  
 **Включение функции AlwaysOn с помощью**  
  
-   [Диспетчер конфигурации SQL Server](#SQLCM2Procedure)  
  
-   [PowerShell](#PScmd2Procedure)  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM2Procedure"></a>Использование диспетчер конфигурации SQL Server  
 **Включение функции «Группы доступности AlwaysOn»**  
  
1.  Выполните подключение к узлу отказоустойчивой кластеризации Windows Server (WSFC), на котором размещен экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], на котором требуется включить группы доступности AlwaysOn.  
  
2.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **Средства настройки**и **Диспетчер конфигурации SQL Server**.  
  
3.  В **Диспетчер конфигурации SQL Server**щелкните **SQL Server службы**, щелкните правой кнопкой мыши SQL Server (** < *`instance name`*>)**, где **<*`instance name`*>** — имя локального экземпляра сервера, для которого требуется включить группы доступности AlwaysOn, и нажмите кнопку **Свойства.**  
  
4.  Перейдите на вкладку **высокий уровень доступности AlwaysOn** .  
  
5.  Убедитесь, что поле **Имя отказоустойчивого кластера Windows** содержит имя локального отказоустойчивого кластера. Если это поле не заполнено, в настоящее время этот экземпляр сервера не поддерживает [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Либо локальный компьютер не является узлом кластера, кластер WSFC завершил работу, либо этот выпуск [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] не поддерживает [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
6.  Установите флажок **включить группы доступности AlwaysOn** и нажмите кнопку **ОК**.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сохранит внесенные изменения. После этого необходимо вручную перезапустить службу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Это позволит выбрать время перезапуска, которое лучше всего подходит под требования вашего предприятия. После перезапуска службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] функция AlwaysOn будет включена, а свойство `IsHadrEnabled` будет установлено в значение 1.  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd2Procedure"></a> Использование SQL Server PowerShell  
 **Включение функции AlwaysOn**  
  
1.  Измените каталог (`cd`) на каталог экземпляра сервера, для которого необходимо включить группы доступности AlwaysOn.  
  
2.  С помощью командлета `Enable-SqlAlwaysOn` включите группы доступности AlwaysOn.  
  
     Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
    > [!NOTE]  
    >  Сведения о том, как управлять тем `Enable-SqlAlwaysOn` , перезапускается ли командлет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , см. в разделе Когда командлет перезапускает [службу SQL Server?](#WhenCmdletRestartsSQL)далее в этой статье.  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="example-enable-sqlalwayson"></a><a name="ExmplEnable-SqlHadrServic"></a> Пример: Enable-SqlAlwaysOn  
 Следующая команда PowerShell включает [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в экземпляре SQL Server (*Computer* \\ *экземпляр*компьютера).  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="disable-alwayson-availability-groups"></a><a name="DisableAOAG"></a>Отключить группы доступности AlwaysOn  
  
-   **Перед отключением AlwaysOn**  
  
     [Рекомендации](#Recommendations)  
  
-   **Отключение AlwaysOn с помощью**  
  
    -   [Диспетчер конфигурации SQL Server](#SQLCM3Procedure)  
  
    -   [PowerShell](#PScmd3Procedure)  
  
-   **Дальнейшие действия.**  [после отключения AlwaysOn](#FollowUp)  
  
> [!IMPORTANT]  
>  Функцию AlwaysOn следует одновременно отключать только для одного экземпляра. После отключения групп доступности AlwaysOn подождите, пока служба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не перезапустится, и только после этого переходите к другому экземпляру.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
 Перед отключением AlwaysOn на экземпляре сервера рекомендуется выполнить следующие действия.  
  
1.  Если на экземпляре сервера в настоящее время размещается первичная реплика группы доступности, которую нужно сохранить, то рекомендуется вручную переключить группу доступности на синхронизированную вторичную реплику, если это возможно. Дополнительные сведения см. в разделе [Выполнение запланированного перехода на другой ресурс вручную для группы доступности (SQL Server)](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).  
  
2.  Удалите все локальные вторичные реплики. Дополнительные сведения см. в разделе [Удаление вторичной реплики из группы доступности (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md).  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM3Procedure"></a>Использование диспетчер конфигурации SQL Server  
 **Отключение функции AlwaysOn**  
  
1.  Выполните подключение к узлу отказоустойчивой кластеризации Windows Server (WSFC), где размещен экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в котором требуется отключить группы доступности AlwaysOn.  
  
2.  В меню **Пуск** наведите указатель на пункт **все программы**, выберите [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] пункт **средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
3.  В **Диспетчер конфигурации SQL Server**щелкните **SQL Server службы**, щелкните правой кнопкой мыши SQL Server (** < *`instance name`*>)**, где **<*`instance name`*>** — имя локального экземпляра сервера, для которого требуется отключить группы доступности AlwaysOn, и нажмите кнопку **Свойства**.  
  
4.  На вкладке**Высокий уровень доступности AlwaysOn**снимите флажок **Включить группы доступности AlwaysOn** и нажмите кнопку **ОК**.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сохранит изменения и перезапустит службу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . После перезапуска службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] функция AlwaysOn будет отключена, а свойство `IsHadrEnabled` будет установлено в значение 0, указывающее на то, группы доступности AlwaysOn отключены.  
  
5.  Рекомендуется ознакомиться с разделом [Дальнейшие действия. После отключения AlwaysOn](#FollowUp)ниже в этой статье.  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd3Procedure"></a> Использование SQL Server PowerShell  
 **Отключение функции AlwaysOn**  
  
1.  Перейдите в каталог ( `cd` ) на экземпляр сервера, включенный в данный момент, который вы хотите включить для группы доступности AlwaysOn.  
  
2.  С помощью командлета `Disable-SqlAlwaysOn` включите группы доступности AlwaysOn.  
  
     Например, следующая команда отключает группы доступности AlwaysOn на экземпляре SQL Server (*Computer* \\ *экземпляре*компьютера).  Эта команда требует перезапуска экземпляра, который будет предложено подтвердить.  
  
    ```powershell
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  Сведения о том, как управлять тем `Disable-SqlAlwaysOn` , перезапускается ли командлет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , см. в разделе Когда командлет перезапускает [службу SQL Server?](#WhenCmdletRestartsSQL)далее в этой статье.  
  
     Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="follow-up-after-disabling-alwayson"></a><a name="FollowUp"></a>Дальнейшие действия. После отключения AlwaysOn  
 После отключения групп доступности AlwaysOn экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо перезапустить. Диспетчер конфигурации SQL Server автоматически перезапускает экземпляр сервера. Но если использовался командлет `Disable-SqlAlwaysOn`, то потребуется перезапустить экземпляр сервера вручную. Дополнительные сведения см. в статье [sqlservr Application](../../../tools/sqlservr-application.md).  
  
 На перезапущенном экземпляре сервера происходит следующее:  
  
-   базы данных обеспечения доступности не запускаются при запуске сервер SQL Server, из-за чего они становятся недоступными.  
  
-   Единственная поддерживаемая инструкция AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] — [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql). Инструкции CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP и параметры SET HADR инструкции ALTER DATABASE не поддерживаются.  
  
-   При отключении групп доступности AlwaysOn метаданные службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и данные конфигурации [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в WSFC не затрагиваются.  
  
 Если нужно полностью отключить группы доступности AlwaysOn в каждом экземпляре сервера, где размещается реплика доступности для одной или нескольких групп доступности, то рекомендуется выполнить следующие действия.  
  
1.  Если перед отключением AlwaysOn локальные реплики доступности не удалялись, удалите все группы доступности, для которых на экземпляре сервера размещается реплика доступности. Сведения об удалении группы доступности см. в разделе [Удаление группы доступности (SQL Server)](remove-an-availability-group-sql-server.md).  
  
2.  Чтобы удалить оставшиеся метаданные, удалите все затронутые группы доступности на экземпляре сервера, который входит в состав исходного кластера WSFC.  
  
3.  Все базы данных-источники остаются доступными для всех подключений, однако синхронизация данных между главной и базами данных-получателями останавливается.  
  
4.  Базы данных-получатели переводятся в состояние RESTORING. Вы можете либо удалить эти базы данных, либо восстановить их при помощи функции RESTORE WITH RECOVERY. Однако восстановленные базы данных больше не будут участвовать в синхронизации данных группы доступности.  
  
##  <a name="when-does-a-cmdlet-restart-the-sql-server-service"></a><a name="WhenCmdletRestartsSQL"></a> Когда командлет перезапускает службу SQL Server?  
 В экземпляре сервера, запущенном в настоящее время, использование командлетов `Enable-SqlAlwaysOn` или `Disable-SqlAlwaysOn` для смены текущей настройки функции AlwaysOn может стать причиной перезапуска службы SQL Server. Алгоритм перезапуска зависит от следующих условий:  
  
|указан параметр -NoServiceRestart;|указан параметр -Force.|Перезапущена ли служба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ?|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|нет|нет|По умолчанию. Однако командлет выводит следующее сообщение:<br /><br /> **Чтобы выполнить это действие, необходимо перезапустить службу SQL Server для экземпляра сервера "<instance_name>". Вы хотите продолжить?**<br /><br /> **[Y] Yes  [N] No  [S] Suspend  [?] Help (значение по умолчанию — "Y"):**<br /><br /> Если указать **N** или **S**, служба не будет перезапущена.|  
|нет|Да|Служба перезапускается.|  
|Да|нет|Служба не перезапускается.|  
|Да|Да|Служба не перезапускается.|  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql)  
