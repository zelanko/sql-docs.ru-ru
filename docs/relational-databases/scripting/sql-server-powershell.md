---
title: "PowerShell для SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 08/04/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89b70725-bbe7-4ffe-a27d-2a40005a97e7
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 19eb632fc1b975671f968b9e2db806129eacae27
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sql-server-powershell"></a>SQL Server PowerShell
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживает Windows PowerShell — многофункциональную оболочку для работы со скриптами, позволяющую администраторам и разработчикам автоматизировать администрирование серверов и развертывание приложений. Язык Windows PowerShell поддерживает более сложные логические конструкции по сравнению со сценариями [!INCLUDE[tsql](../../includes/tsql-md.md)] , что дает администраторам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возможность создавать надежно работающие сценарии администрирования. Сценарии Windows PowerShell также можно использовать для администрирования других серверных продуктов [!INCLUDE[msCoName](../../includes/msconame-md.md)] . В результате администраторы получают возможность использовать общий язык сценариев для разных серверов.  
  
## <a name="sql-server-powershell-components"></a>Компоненты SQL Server PowerShell  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет модуль Windows PowerShell, называемый **sqlps** , который используется для импорта компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среду Windows PowerShell или скрипт. Модуль **splps** загружает две оснастки Windows PowerShell, которые реализуют следующие объекты.  
  
-   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который предоставляет простой механизм навигации, аналогичный путям в файловой системе. Можно построить пути, аналогичные путям файловой системы, где диску соответствует управляющая объектная модель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а узлы основаны на классах объектной модели. Затем можно использовать привычные команды, такие как **cd** и **dir** , чтобы перемещаться по путям, аналогично переходу по структуре папок в окне командной строки. Для выполнения действий на узлах пути можно использовать другие команды, например **ren** или **del**.  
  
-   Набор командлетов, которые являются командами, используемыми в сценариях Windows PowerShell для указания действия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Командлеты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживают такие действия, как запуск скрипта **sqlcmd** , содержащего инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] или XQuery.  
  
 Дополнительные сведения о Windows PowerShell см. в разделе [Приступая к работе с Windows PowerShell](https://msdn.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell).  
  
## <a name="sql-server-versions"></a>SQL Server, версии  
 Компоненты PowerShell [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] могут использоваться для управления экземплярами [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] и более поздних версий. На экземплярах [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] должен быть запущен пакет обновления 2 (SP2) или более поздние версии. На экземплярах [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] должен быть запущен пакет обновления 4 (SP4) или более поздние версии. Если компоненты PowerShell [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] используются в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то в них поддерживаются только те функции, которые доступны в этих версиях.  
     
## <a name="sql-server-powershell-tasks"></a>Задачи SQL Server PowerShell  
  
|Описание задачи|Раздел|  
|----------------------|-----------| 
|Установка расширений Microsoft® Windows PowerShell для Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  При установке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]расширения PowerShell устанавливаются по умолчанию.  Можно вручную установить расширения PowerShell для SQL Server 2016, установив следующие компоненты из пакета дополнительных компонентов Microsoft® SQL Server® 2016:<br/>     Microsoft® System CLR Types для Microsoft SQL Server® 2016 (SQLSysClrTypes.msi)<br/>Общие управляющие объекты Microsoft® SQL Server® 2016 (SharedManagementObjects.msi)<br/> Расширения Microsoft® Windows PowerShell для Microsoft SQL Server® 2016 (PowerShellTools.msi)|[Пакет дополнительных компонентов Microsoft® SQL Server® 2016](https://www.microsoft.com/en-us/download/details.aspx?id=52676).   | 
|Описание предпочтительного механизма запуска компонентов PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; открытия сеанса PowerShell и загрузки модуля **sqlps** . Модуль **sqlps** загружает в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик PowerShell, командлеты и сборки управляющих объектов SQL Server (SMO), используемые поставщиком и командлетами.|[Импорт модуля SQLPS](../../relational-databases/scripting/import-the-sqlps-module.md)|  
|Описание способа загрузки только сборок объектов SMO без поставщика и командлетов.|[Загрузка сборки объектов SMO в Windows PowerShell](../../relational-databases/scripting/load-the-smo-assemblies-in-windows-powershell.md)|  
|Описание способа запуска сеанса Windows PowerShell щелчком правой кнопкой мыши узла в **обозревателе объектов**. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] запускает сеанс Windows Powershell, загружает модуль **sqlps** и настраивает путь поставщика SQL Server для выделенного объекта.|[Запуск Windows PowerShell из среды SQL Server Management Studio](../../relational-databases/scripting/run-windows-powershell-from-sql-server-management-studio.md)|  
|Описание создания шагов задания агента SQL Server для запуска скрипта Windows PowerShell. Пользователь может планировать выполнение заданий в указанное время или в ответ на события.|[Использование Windows PowerShell в шагах агента SQL Server](../../relational-databases/scripting/run-windows-powershell-steps-in-sql-server-agent.md)|  
|Описание использования поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для перемещения по иерархии объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Поставщик SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell-provider.md)|  
|Описание использования командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , содержащих действия компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , например запуск скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] .|[Использование командлетов компонента Database Engine](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)|  
|Описание способа указания идентификаторов с разделителями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , содержащих символы, не поддерживаемые в Windows PowerShell.|[Идентификаторы SQL Server в PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)|  
|Описание создания подключения с проверкой подлинности SQL Server. По умолчанию компоненты SQL Server PowerShell используют подключение с помощью проверки подлинности Windows и учетных данных процесса, в котором выполняется Windows PowerShell.|[Управление проверкой подлинности в компонент Database Engine PowerShell](../../relational-databases/scripting/manage-authentication-in-database-engine-powershell.md)|  
|Описание использования переменных, реализованных поставщиком SQL Server PowerShell, для управления количеством объектов, перечисляемых при использовании функции завершения по клавише TAB в Windows PowerShell. Это особенно полезно при работе с базами данных, содержащими большое количество объектов.|[Управление завершением по нажатию клавиши Tab (SQL Server PowerShell)](../../relational-databases/scripting/manage-tab-completion-sql-server-powershell.md)|  
|Описание использования командлета Get-Help для получения сведений о компонентах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде Windows PowerShell.|[Получение справок по SQL Server PowerShell](../../relational-databases/scripting/get-help-sql-server-powershell.md)|  
  
  
