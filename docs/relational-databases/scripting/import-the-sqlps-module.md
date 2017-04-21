---
title: "Импорт модуля SQLPS | Документация Майкрософт"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 39b5b945994c9531deb3d545dbb438657b1914fe
ms.lasthandoff: 04/11/2017

---
# <a name="import-the-sqlps-module"></a>Импорт модуля SQLPS
  Для управления сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из PowerShell рекомендуется импортировать модуль **sqlps** в среду Windows PowerShell. Модуль загружает и регистрирует оснастки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сборки управляемости.  Начиная с Windows PowerShell 3.0, модули импортируются автоматически, когда любой командлет или любая функция из модуля используются в команде. Эта возможность работает для любого модуля в каталоге, включенного в значение переменной среды PSModulePath.  Дополнительные сведения см. в разделе [Импорт модуля PowerShell](https://msdn.microsoft.com/library/dd878284(v=vs.85).aspx)
  
1.  **Before You Begin:**  [Security](#Security)  
  
2.  **To load the module:**  [Load the sqlps Module](#LoadSqlps)  
  
## <a name="before-you-begin"></a>Перед началом  
 После импорта модуля **sqlps** в среду Windows PowerShell можно:  
  
-   Вводить команды Windows PowerShell в интерактивном режиме.  
  
-   Запускать файлы скриптов Windows PowerShell.  
  
-   Запускать командлеты служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Использовать пути поставщика служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для передвижения по иерархии объектов среды служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Для управления объектами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте объектные модели управляемости [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (такие как Microsoft.SqlServer.Management.Smo).  
  
> [!NOTE]  
>  Команды, используемые в именах двух командлетов SQL Server (**Encode-Sqlname** и **Decode-Sqlname**), не соответствуют утвержденным командам для Windows PowerShell. Это не влияет на их работу, однако среда Windows PowerShell выдает предупреждение при импорте модуля **sqlps** в сеанс.  
  
###  <a name="Security"></a> Безопасность  
 По умолчанию в Windows PowerShell политика выполнения скриптов работает в **ограниченном**режиме, блокируя все скрипты Windows PowerShell. Чтобы загрузить модуль **sqlps** , с помощью командлета **Set-ExecutionPolicy** разрешите выполнение подписанных или всех скриптов. Следует выполнять только скрипты, полученные из доверенных источников, а также защищать все входные и выходные файлы, установив необходимые разрешения NTFS. Дополнительные сведения о включении скриптов Windows PowerShell см. в разделе [Выполнение скриптов Windows PowerShell](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx).  
  
##  <a name="LoadSqlps"></a> Загрузка модуля sqlps  
 **Загрузка модуля sqlps в среду Windows PowerShell**  
  
1.  Чтобы установить соответствующую политику выполнения скриптов, используйте командлет **Set-ExecutionPolicy** .  
  
2.  Для импорта модуля sqlps используйте командлет **Import-Module** . Если требуется отключить предупреждение о **Encode-Sqlname** и **Decode-Sqlname** , задайте параметр **DisableNameChecking**.  
  
### <a name="example"></a>Пример  
 В этом примере показана загрузка модуля **sqlps** с отключенной проверкой имен.  
  
```powershell 
# Import the SQL Server Module.    
Import-Module Sqlps -DisableNameChecking;

# To check whether the module is installed.
Get-Module -ListAvailable -Name Sqlps;
```  
  
> [!NOTE]  
>  Если модуля **sqlps** нет в указанном расположении, перейдите в расположение модуля или укажите в скрипте полный путь (если имена папок в пути содержат пробелы, возьмите путь в двойные кавычки). Модуль **sqlps** находится в папке Tools\Powershell для экземпляра SQL Server.  
  
 ![Значок стрелки, используемый для ссылки возврата в начало](../../analysis-services/instances/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[&#91;В начало&#93;]()  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Использование командлетов компонента Database Engine](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
 [Установка модуля PowerShell](https://msdn.microsoft.com/library/dd878350(v=vs.85).aspx)  
 [Import-Module](https://technet.microsoft.com/library/hh849725.aspx)
  
  

