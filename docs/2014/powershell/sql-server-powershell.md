---
title: PowerShell для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 89b70725-bbe7-4ffe-a27d-2a40005a97e7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: acfa87245449566c1f91b447910f5194eda192b0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62922588"
---
# <a name="sql-server-powershell"></a>SQL Server PowerShell
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] поддерживает Windows PowerShell — многофункциональную оболочку для работы со скриптами, позволяющую администраторам и разработчикам автоматизировать администрирование серверов и развертывание приложений. Язык Windows PowerShell поддерживает более сложные логические конструкции по сравнению со сценариями [!INCLUDE[tsql](../includes/tsql-md.md)] , что дает администраторам [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] возможность создавать надежно работающие сценарии администрирования. Сценарии Windows PowerShell также можно использовать для администрирования других серверных продуктов [!INCLUDE[msCoName](../includes/msconame-md.md)] . В результате администраторы получают возможность использовать общий язык сценариев для разных серверов.  
  
## <a name="sql-server-powershell-components"></a>Компоненты SQL Server PowerShell  
 В состав [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] входит модуль Windows PowerShell, называемый `sqlps`, который используется для импорта компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в среду Windows PowerShell 2.0 или скрипт. Модуль `sqlps` загружает две оснастки Windows PowerShell, которые реализуют следующие объекты.  
  
-   Поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , который предоставляет простой механизм навигации, аналогичный путям в файловой системе. Можно построить пути, аналогичные путям файловой системы, где диску соответствует управляющая объектная модель [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , а узлы основаны на классах объектной модели. Затем можно использовать привычные команды, такие как **cd** и **dir** , чтобы перемещаться по путям, аналогично переходу по структуре папок в окне командной строки. Для выполнения действий на узлах пути можно использовать другие команды, например **ren** или **del**.  
  
-   Набор командлетов, которые являются командами, используемыми в сценариях Windows PowerShell для указания действия [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Командлеты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживают такие действия, как запуск скрипта **sqlcmd** , содержащего инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] или XQuery.  
  
 Дополнительные сведения о Windows PowerShell см. в разделе [Руководство по началу работы с Windows PowerShell](https://msdn.microsoft.com/library/hh857337.aspx).  
  
## <a name="sql-server-versions"></a>SQL Server, версии  
 Компоненты PowerShell [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] могут использоваться для управления экземплярами [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] и более поздних версий. На экземплярах [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] должен быть запущен пакет обновления 2 (SP2) или более поздние версии. На экземплярах [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] должен быть запущен пакет обновления 4 (SP4) или более поздние версии. Если компоненты PowerShell [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] используются в более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], то в них поддерживаются только те функции, которые доступны в этих версиях.  
  
## <a name="sql-server-powershell-tasks"></a>Задачи SQL Server PowerShell  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описание предпочтительного механизма для запуска компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell, открытия сеанса PowerShell и загрузки модуля `sqlps`. Модуль `sqlps` загружает в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поставщик PowerShell, командлеты и сборки управляющих объектов SQL Server (SMO), используемые поставщиком и командлетами.|[Импорт модуля SQLPS](../database-engine/import-the-sqlps-module.md)|  
|Описание способа загрузки только сборок объектов SMO без поставщика и командлетов.|[Загрузка сборки объектов SMO в Windows PowerShell](load-the-smo-assemblies-in-windows-powershell.md)|  
|Описание способа запуска сеанса Windows PowerShell щелчком правой кнопкой мыши узла в **обозревателе объектов**. [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]запускает сеанс Windows PowerShell, загружает `sqlps` модуль и задает путь поставщика SQL Server к выбранному объекту.|[Запуск Windows PowerShell из среды SQL Server Management Studio](run-windows-powershell-from-sql-server-management-studio.md)|  
|Описание создания шагов задания агента SQL Server для запуска скрипта Windows PowerShell. Пользователь может планировать выполнение заданий в указанное время или в ответ на события.|[Использование Windows PowerShell в шагах агента SQL Server](run-windows-powershell-steps-in-sql-server-agent.md)|  
|Описание использования поставщика [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для перемещения по иерархии объектов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[Поставщик SQL Server PowerShell](sql-server-powershell-provider.md)|  
|Описание использования командлетов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , содержащих действия компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , например запуск скрипта [!INCLUDE[tsql](../includes/tsql-md.md)] .|[Использование командлетов компонента Database Engine](../database-engine/use-the-database-engine-cmdlets.md)|  
|Описание способа указания идентификаторов с разделителями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , содержащих символы, не поддерживаемые в Windows PowerShell.|[Идентификаторы SQL Server в PowerShell](sql-server-identifiers-in-powershell.md)|  
|Описание создания подключения с проверкой подлинности SQL Server. По умолчанию компоненты SQL Server PowerShell используют подключение с помощью проверки подлинности Windows и учетных данных процесса, в котором выполняется Windows PowerShell.|[Управление проверкой подлинности в компонент Database Engine PowerShell](manage-authentication-in-database-engine-powershell.md)|  
|Описание использования переменных, реализованных поставщиком SQL Server PowerShell, для управления количеством объектов, перечисляемых при использовании функции завершения по клавише TAB в Windows PowerShell. Это особенно полезно при работе с базами данных, содержащими большое количество объектов.|[Управление завершением по нажатию клавиши Tab (SQL Server PowerShell)](manage-tab-completion-sql-server-powershell.md)|  
|Описание использования командлета Get-Help для получения сведений о компонентах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в среде Windows PowerShell.|[Получение справок по SQL Server PowerShell](../database-engine/get-help-sql-server-powershell.md)|  
  
  
