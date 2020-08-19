---
description: Удаление приложения уровня данных
title: Удаление приложения уровня данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.deletedacwizard.deletedac.f1
- sql13.swb.deletedacwizard.summary.f1
- sql13.swb.deletedacwizard.introduction.f1
- sql13.swb.deletedacwizard.choosemethod.f1
helpviewer_keywords:
- How to [DAC], delete
- data-tier application [SQL Server], delete
- wizard [DAC], delete
- delete DAC
ms.assetid: 16fe1c18-4486-424d-81d6-d276ed97482f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2bde888ff6091ae8d05445acce1afb1469843c18
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386640"
---
# <a name="delete-a-data-tier-application"></a>Удаление приложения уровня данных
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Для удаления приложения уровня данных (DAC) используйте мастер удаления приложения уровня данных или скрипт Windows PowerShell. Можно указать, будет ли связанная база данных сохранена, отсоединена или уничтожена.  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Обновление приложения уровня данных с использованием:**  [Мастер регистрации приложения уровня данных](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)  
  
## <a name="before-you-begin"></a>Перед началом  
 При удалении экземпляра приложения уровня данных (DAC) можно выбрать один из трех параметров, которые определяют действие над базой данных, связанной с этим приложением уровня данных. При использовании любого из трех параметров удаляются метаданные определения DAC. Различие между ними состоит в действиях, которые они выполняют с базой данных, связанной с приложением уровня данных. Мастер не удаляет ни один из объектов уровня экземпляра, связанных с DAC или базой данных, таких как имена входа.  
  
|Параметр|Операции базы данных|  
|------------|----------------------|  
|Регистрация удаления|Связанная база данных остается неизменной.|  
|Отсоединение базы данных|Выполняется отсоединение связанной базы данных. Экземпляр компонента Database Engine не может ссылаться на эту базу данных, но данные и файлы журналов сохраняются целыми.|  
|Удаление базы данных|Связанная база данных уничтожается. Происходит удаление данных и файлов журналов.|  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Ограничения  
 Автоматический механизм восстановления метаданных определения приложения уровня данных или базы данных после удаления приложения уровня данных отсутствует. Способ, как можно будет вручную перестроить экземпляр приложения уровня данных, зависит от параметра удаления.  
  
|Параметр|Повторное создание экземпляра приложения уровня данных|  
|------------|-------------------------------------|  
|Регистрация удаления|Зарегистрируйте приложение уровня данных из оставшейся базы данных.|  
|Отсоединение базы данных|Повторно присоедините базу данных с помощью команды **sp_attachdb** или среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем зарегистрируйте новый экземпляр приложения уровня данных из базы данных.|  
|Удаление базы данных|Восстановите базу данных из полной резервной копии, созданной до удаления приложения уровня данных, а затем зарегистрируйте новый экземпляр приложения уровня данных из базы данных.|  
  
> [!WARNING]  
>  При повторном создании экземпляра приложения уровня данных путем его регистрации из восстановленной или повторно присоединенной базы данных некоторые части исходного приложения уровня данных, например политика выбора сервера, не создаются повторно.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Приложение уровня данных (DAC) может быть удалено только членами предопределенных ролей сервера **sysadmin** и **serveradmin** или владельцем базы данных. Этот мастер также может быть запущен от имени учетной записи системного администратора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем **sa** .  
  
##  <a name="using-the-delete-data-tier-application-wizard"></a><a name="UsingDeleteDACWizard"></a> Использование мастера удаления приложения уровня данных  
 **Удаление приложения уровня данных с помощью мастера**  
  
1.  В **Обозревателе объектов**разверните узел экземпляра, содержащего приложение уровня данных, которое требуется удалить.  
  
2.  Разверните узел **Управление** .  
  
3.  Разверните узел **Приложения уровня данных** .  
  
4.  Щелкните правой кнопкой мыши приложение уровня данных, которое требуется удалить, и выберите пункт **Удалить приложение уровня данных...**.  
  
5.  Выполните шаги в диалоговых окнах мастера.  
  
    1.  [Введение](#Introduction)  
  
    2.  [Выбор метода](#Choose_method)  
  
    3.  [Сводка](#Summary)  
  
    4.  [Удалить приложение уровня данных](#Delete_datatier_application)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> Вводная страница  
 На этой странице описаны шаги удаления приложения уровня данных.  
  
 **Больше не показывать эту страницу.** — щелкните этот флажок, чтобы предотвратить отображение этой страницы в будущем.  
  
 **Далее >** — переход к странице **Выбор метода**.  
  
 **Отмена** — отмена действий мастера без удаления приложения уровня данных или базы данных.  
  
 [Использование мастера удаления приложения уровня данных](#UsingDeleteDACWizard)  
  
##  <a name="choose-method-page"></a><a name="Choose_method"></a> Страница «Выбор метода»  
 Используйте данную страницу, чтобы указать параметр для обработки связанной с удаляемым приложением уровня данных базы данных.  
  
 **Регистрация удаления** удаляет метаданные, определяющие приложение уровня данных, но оставляет неизменной связанную базу данных.  
  
 **Отсоединение базы данных** — удаляет метаданные, определяющие приложение уровня данных, и отсоединяет связанную базу данных.  
  
 На эту базу данных больше нельзя будет ссылаться из экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], но данные и файлы журнала останутся неизменными.  
  
 **Удаление базы данных** — производится удаление метаданных, определяющих DAC, и уничтожение связанной базы данных.  
  
 Удаление данных и файлов журналов, относящихся к базе данных, осуществляется на постоянной основе.  
  
 **< Назад** — возврат на страницу **Введение**.  
  
 **Далее >** — переход к странице **Сводка**.  
  
 **Отмена** — завершение работы мастера без удаления DAC или базы данных.  
  
 [Использование мастера удаления приложения уровня данных](#UsingDeleteDACWizard)  
  
##  <a name="summary-page"></a><a name="Summary"></a> Страница «Сводка»  
 На этой странице можно просмотреть действия, которые будут выполнены мастером при удалении экземпляра приложения уровня данных.  
  
 **Просмотр сводки по своему выбору** — предоставляет возможность ознакомиться со сведениями о DAC, базе данных и методе удаления, отображенными в этом окне. Если эти сведения правильны, выберите **Далее** или **Готово** , чтобы удалить DAC. Если сведения о DAC и базе данных неверны, выберите **Отмена** и правильно укажите DAC. Если неверным является метод удаления, нажмите кнопку **Назад** , чтобы вернуться к странице **Выбор метода** , и укажите другой метод.  
  
 **< Назад** — возврат к странице **Выбор метода** для выбора другого метода удаления.  
  
 **Далее >** — удаление экземпляра приложения уровня данных методом, выбранным на предыдущей странице, и переход к странице **Удаление приложения уровня данных**.  
  
 **Отмена** — завершение работы мастера без удаления экземпляра приложения уровня данных или базы данных.  
  
 [Использование мастера удаления приложения уровня данных](#UsingDeleteDACWizard)  
  
##  <a name="delete-data-tier-application-page"></a><a name="Delete_datatier_application"></a> Страница «Удаление приложения уровня данных»  
 Эта страница сообщает об успешном или неуспешном завершении операции удаления.  
  
 **Удаление приложения уровня данных** — сообщает об успехе или неуспехе каждого действия, предпринятого для удаления экземпляра приложения уровня данных. Просмотрите эти сведения, чтобы выяснить результаты каждого действия. Для каждого действия, в котором обнаружена ошибка, предусмотрена ссылка в столбце **Результат** . Выберите эту ссылку, чтобы просмотреть отчет об ошибках, относящихся данному действию.  
  
 **Сохранить отчет** — сохранить отчет об удалении в HTML-файле. В этом файле содержится отчет о состоянии каждого из действий, в том числе все выданные сообщения об ошибках. По умолчанию используется папка «SQL Server Management Studio\DAC Packages», вложенная в папку Documents рабочего каталога учетной записи пользователя Windows.  
  
 **Готово** — завершение работы мастера.  
  
 [Использование мастера удаления приложения уровня данных](#UsingDeleteDACWizard)  
  
##  <a name="using-powershell"></a><a name="DeleteDACPowerShell"></a> Использование PowerShell  

1. Создайте объект SMO Server и задайте его экземпляру, содержащему приложение уровня данных, которое требуется удалить.  
  
1. Откройте объект **ServerConnection** и подключитесь к тому же экземпляру.  
  
1. Используйте `add_DacActionStarted` и `add_DacActionFinished` для подписки на обновление событий приложения уровня данных.  
  
1. Укажите приложение уровня данных, которое требуется удалить.  
  
1. Используйте один из трех примеров в зависимости от того, какой из вариантов удаления является подходящим:  
  
   - Для удаления регистрации приложения уровня данных без изменения базы данных используйте метод `Unmanage`.  
   - Для удаления регистрации приложения уровня данных и отсоединения базы данных используйте метод `Uninstall` и укажите `DetachDatabase`.  
   - Для удаления регистрации приложения уровня данных и сброса базы данных используйте метод `Uninstall` и укажите `DropDatabase`.
  
### <a name="delete-the-dac-and-leave-the-database"></a>Удаление приложения уровня данных без изменения базы данных

В приведенном ниже примере рассматривается удаление приложения уровня данных с именем `<myApplication>` с помощью метода `Unmanage`, который позволяет удалить приложение уровня данных без изменения базы данных.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$server = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverConnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($server.ConnectionContext.SqlConnectionObject)  
$serverConnection.Connect()  
$dacStore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverConnection)  
  
## Subscribe to the DAC delete events.  
$dacStore.add_DacActionStarted({Write-Host `n`nStarting at $(Get-Date) :: $_.Description})  
$dacStore.add_DacActionFinished({Write-Host Completed at $(Get-Date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "<myApplication>"  
  
## Only delete the DAC definition from msdb, the associated database remains active.  
$dacStore.Unmanage($dacName)  
```
  
### <a name="delete-the-dac-and-detach-the-database"></a>Удаление приложения уровня данных с отсоединением базы данных

В приведенном ниже примере рассматривается удаление приложения уровня данных с именем `<myApplication>` с помощью метода `Uninstall`, который позволяет удалить приложение уровня данных с отсоединением базы данных.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$server = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverConnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($server.ConnectionContext.SqlConnectionObject)  
$serverConnection.Connect()  
$dacStore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverConnection)  
  
## Subscribe to the DAC delete events.  
$dacStore.add_DacActionStarted({Write-Host `n`nStarting at $(Get-Date) :: $_.Description})  
$dacStore.add_DacActionFinished({Write-Host Completed at $(Get-Date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "<myApplication>"  
  
## Delete the DAC definition from msdb and detach the associated database.  
$dacStore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DetachDatabase)  
```
  
### <a name="delete-the-dac-and-drop-the-database"></a>Удаление приложения уровня данных с удалением базы данных

В приведенном ниже примере рассматривается удаление приложения уровня данных с именем `<myApplication>` с помощью метода `Uninstall`, который позволяет удалить приложение уровня данных и базу данных.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$server = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverConnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($server.ConnectionContext.SqlConnectionObject)  
$serverConnection.Connect()  
$dacStore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverConnection)  
  
## Subscribe to the DAC delete events.  
$dacStore.add_DacActionStarted({Write-Host `n`nStarting at $(Get-Date) :: $_.Description})  
$dacStore.add_DacActionFinished({Write-Host Completed at $(Get-Date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "<myApplication>"  
  
## Delete the DAC definition from msdb and drop the associated database.  
$dacStore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DropDatabase)  
```
  
## <a name="see-also"></a>См. также:  
 [Приложения уровня данных](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Приложения уровня данных](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Развертывание приложения уровня данных](../../relational-databases/data-tier-applications/deploy-a-data-tier-application.md)   
 [Регистрация базы данных в качестве приложения уровня данных](../../relational-databases/data-tier-applications/register-a-database-as-a-dac.md)   
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
