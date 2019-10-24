---
title: Проверка пакета приложения уровня данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], validate
- data-tier application [SQL Server], compare
- validate DAC
- compare DACs
- data-tier application [SQL Server], view
- view DAC
ms.assetid: 726ffcc2-9221-424a-8477-99e3f85f03bd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56655f7d75635668d266b44853fc29969fd741ed
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72782671"
---
# <a name="validate-a-dac-package"></a>Проверка пакета приложения уровня данных
  Перед развертыванием пакета приложения уровня данных рекомендуется просмотреть его содержимое и проверить действия по обновлению перед обновлением существующего пакета приложения уровня данных. Тем более это истина для развертывания пакетов, которые ранее в организации не развертывались.  
  
1.  **Before you begin:**  [Prerequisites](#Prerequisites)  
  
2.  **Обновление приложения уровня данных с использованием следующих средств:**  [просмотр содержимого приложения уровня данных](#ViewDACContents), [просмотр изменений базы данных](#ViewDBChanges), [просмотр действий по обновлению](#ViewUpgradeActions), [Compare DACs](#CompareDACs)  
  
##  <a name="Prerequisites"></a> предварительные требования  
 Рекомендуется не выполнять развертывание пакетов DAC, полученных из неизвестных или ненадежных источников. В этих пакетах может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы. Прежде чем использовать приложение уровня данных, полученное из ненадежного источника, разверните его на изолированном тестовом экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], выполните для базы данных инструкцию [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql), а также изучите исходный код в базе данных, например хранимые процедуры и другой определенный пользователем код.  
  
##  <a name="ViewDACContents"></a> просмотр содержимого приложения уровня данных  
 Просматривать содержимое пакета приложения уровня данных можно с помощью двух механизмов. Можно импортировать пакет приложения уровня данных в проект приложения уровня данных в средствах разработчика SQL Server. Можно распаковать содержимое пакета в папку.  
  
 **Просмотр приложения уровня данных в средствах разработчика SQL Server**  
  
1.  Откройте меню **Файл**, выберите **Создать**, затем **Проект...** .  
  
2.  Выберите шаблон проекта **SQL Server** и укажите **Имя**, **Расположение**и **Имя решения**.  
  
3.  В **обозревателе решений** щелкните правой кнопкой мыши узел проекта и выберите пункт **Свойства**.  
  
4.  На вкладке **Параметры проекта** в разделе **Типы вывода** установите флажок **Приложение уровня данных (файл с расширением DACPAC)** и закройте диалоговое окно свойств.  
  
5.  В **обозревателе решений** щелкните правой кнопкой мыши узел проекта и выберите **Импорт приложения уровня данных...** .  
  
6.  Используйте **Обозреватель решений** , чтобы открыть любые файлы в приложении уровня данных, например политику выбора сервера, а также скрипты, выполняемые до и после развертывания.  
  
7.  Используйте **Представление схемы** , чтобы просмотреть все объекты, составляющие схему, обращая особое внимание на код таких объектов, как функции или хранимые процедуры.  
  
 **Просмотр приложения уровня данных в папке**  
  
-   Распакуйте пакет приложения уровня данных в папку, следуя инструкциям в [Unpack a DAC Package](unpack-a-dac-package.md).  
  
-   Просмотрите содержимое скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , открывая их в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
-   Просмотрите содержимое текстовых файлов с помощью таких средств, как Блокнот.  
  
##  <a name="ViewDBChanges"></a> просмотр изменений базы данных  
 Непосредственно в связанной базе данных после развертывания текущей версии приложения уровня данных на рабочем сервере могут быть выполнены изменения, конфликтующие со схемой, которая определена в новой версии приложения уровня данных. Прежде чем обновлять приложение уровня данных, проверьте, могут ли изменения, внесенные в базу данных, повлиять на процесс обновления.  
  
 **Просмотр изменений базы данных с помощью мастера**  
  
1.  Запустите мастер **обновления приложения уровня данных** , указав текущую развернутую версию приложения уровня данных и пакет приложения уровня данных, содержащий новую версию приложения уровня данных.  
  
2.  На странице **Обнаружение изменений** просмотрите отчет об изменениях, которые были выполнены в базе данных.  
  
3.  Выберите **Отмена** , если не желаете продолжать обновление.  
  
4.  Дополнительные сведения об использовании мастера см. в разделе [Обновление приложения уровня данных](upgrade-a-data-tier-application.md).  
  
### <a name="view-database-changes-by-using-powershell"></a>Просмотр изменений базы данных с помощью PowerShell
  
1.  Создайте объект SMO Server и задайте его равным экземпляру, содержащему приложение уровня данных, которое требуется просмотреть.  
  
2.  Откройте объект `ServerConnection` и подключитесь к тому же экземпляру.  
  
3.  Укажите имя приложения уровня данных в переменной.  
  
4.  Используйте метод `GetDatabaseChanges()` для вызова объекта `ChangeResults` и направьте объект по каналу в текстовый файл, чтобы сформировать простой отчет о новых, удаленных и измененных объектах.  
  
### <a name="view-database-changes-example-powershell"></a>Просмотр примера изменений базы данных (PowerShell)
  
 В следующем примере сообщается о любых изменениях в базе данных, которые были выполнены в развернутом приложении уровня данных с именем MyApplicaiton.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the change list and save to file.  
$dacChanges = $dacstore.GetDatabaseChanges($dacName) | Out-File -Filepath C:\DACScripts\MyApplicationChanges.txt  
```  
  
##  <a name="ViewUpgradeActions"></a> просмотр действий по обновлению  
 Перед использованием новой версии пакета приложения уровня данных для обновления приложения уровня данных, которое было развернуто из пакета приложения уровня данных более ранней версии, можно создать отчет, содержащий инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые будут выполняться при обновлении, а затем просмотреть эти инструкции.  
  
 **Действия по обновлению отчета с помощью мастера**  
  
1.  Запустите мастер **обновления приложения уровня данных** , указав текущую развернутую версию приложения уровня данных и пакет приложения уровня данных, содержащий новую версию приложения уровня данных.  
  
2.  На странице **Сводка** просмотрите отчет о действиях обновления.  
  
3.  Выберите **Отмена** , если не желаете продолжать обновление.  
  
4.  Дополнительные сведения об использовании мастера см. в разделе [Обновление приложения уровня данных](upgrade-a-data-tier-application.md).  
  
 **Действия по обновлению отчета с помощью PowerShell**  
  
1.  Создайте объект SMO Server и задайте его равным экземпляру, содержащему развернутое приложение уровня данных.  
  
2.  Откройте объект `ServerConnection` и подключитесь к тому же экземпляру.  
  
3.  Используйте `System.IO.File` для загрузки файла пакета приложения уровня данных.  
  
4.  Укажите имя приложения уровня данных в переменной.  
  
5.  Используйте метод `GetIncrementalUpgradeScript()` для получения списка инструкций Transact-SQL, которые будут выполняться при обновлении, и направьте этот список по каналу в текстовый файл.  
  
6.  Закройте файловый поток, используемый для чтения файла пакета приложения уровня данных.  
  
### <a name="view-upgrade-actions-example-powershell"></a>Просмотр примера действий по обновлению (PowerShell)
  
 Следующий пример предоставляет сведения об инструкциях Transact-SQL, которые будут выполняться для обновления приложения уровня данных с именем MyApplicaiton с переходом на схему, указанную в файле MyApplicationVNext.dacpac.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the upgrade script and save to file.  
$dacstore.GetIncrementalUpgradeScript($dacName, $dacType) | Out-File -Filepath C:\DACScripts\MyApplicationUpgrade.sql  
  
## Close the filestream to the new DAC package.  
$fileStream.Close()  
```  
  
##  <a name="CompareDACs"></a> Compare DACs  
 Перед обновлением приложения уровня данных рекомендуется проанализировать различия в базе данных и объектах уровня экземпляра между текущим и новым приложениями уровня данных. В случае отсутствия копии пакета действующего приложения уровня данных его можно извлечь из текущей базы данных.  
  
 Если импортировать оба пакета приложений уровня данных в проекты приложений уровня данных в средствах разработчика SQL Server, то для анализа различий между ними станет возможным использовать средство «Сравнение схем».  
  
 Можно также распаковать приложения уровня данных в отдельные папки. После этого проанализировать различия можно будет с помощью средства поиска отличий, например программы WinDiff.  
  
## <a name="see-also"></a>См. также статью  
 [Приложения уровня данных](data-tier-applications.md)   
 [Развертывание приложения уровня данных](deploy-a-data-tier-application.md)   
 [Обновление приложения уровня данных](upgrade-a-data-tier-application.md)  
