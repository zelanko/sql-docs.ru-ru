---
title: Обновление пакетов служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, migrating
- migrating packages [Integration Services]
ms.assetid: 68dbdf81-032c-4a73-99f6-41420e053980
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 002ef268bbb858db961862c1a30479a3e8462237
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136064"
---
# <a name="upgrade-integration-services-packages"></a>Обновление пакетов служб Integration Services
  При обновлении экземпляра [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] для текущего выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], существующие [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] пакеты не будут автоматически обновлены до формата пакетов, используемого в текущем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] использует. Необходимо будет выбрать метод обновления и обновить эти пакеты вручную.  
  
 При обновлении пакета [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] переносит скрипт в любой задаче "Скрипт" и компоненте скрипта в набор средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для работы с приложениями (VSTA). В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] скрипты в задачах "Скрипт" или компонентах Script использовали среду [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSA). Дополнительные сведения об изменениях, которые может потребоваться внести в скрипт перед выполнением миграции, а также об ошибках их преобразования см. в разделе [Миграция скриптов в VSTA](../../sql-server/install/migrate-scripts-to-vsta.md).  
  
 Сведения об обновлении пакетов при преобразовании проекта в модель развертывания проекта см. в разделе [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).  
  
## <a name="sql-server-2000-data-transformation-services-packages"></a>Пакеты служб DTS в SQL Server 2000  
 В текущей версии служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]не поддерживается миграция или запуск пакетов служб Data Transformation Services (DTS). Следующие функциональные возможности служб DTS более не поддерживаются.  
  
-   Среда выполнения DTS  
  
-   API-интерфейс служб DTS  
  
-   Мастер миграции пакетов служб DTS, выполняющий перенос пакетов DTS в следующую версию служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Поддержка обслуживания пакета служб DTS в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   Задача «Выполнение пакета служб DTS 2000»  
  
-   Сканирование пакетов DTS, выполняемое помощником по обновлению.  
  
 Для миграции пакетов служб DTS доступны следующие параметры.  
  
-   Переместите пакеты в службы [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] или [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], а затем обновите их до версии [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].  
  
     Дополнительные сведения о миграции пакетов служб DTS в [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] и [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] см. в разделах [Миграция пакетов служб DTS](http://go.microsoft.com/fwlink/?LinkId=251870) (2005) и [Миграция пакетов служб DTS](http://go.microsoft.com/fwlink/?LinkId=251871) (2008).  
  
-   Повторно создайте пакеты служб DTS с помощью [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].  
  
     Сведения о новых функциях [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] см. в разделе [Новые возможности (службы Integration Services)](../what-s-new-in-integration-services-in-sql-server-2016.md). Общие сведения о структуре пакетов [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Пакеты служб Integration Services (SSIS)](../integration-services-ssis-packages.md).  
  
## <a name="selecting-an-upgrade-method"></a>Выбор метода обновления  
 Можно использовать различные методы обновления пакетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] . Для некоторых из этих методов обновление лишь временное. Для других — обновление постоянное. В следующей таблице описан каждый из этих методов и указано, является обновление временным или постоянным.  
  
> [!NOTE]  
>  При запуске пакета [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с помощью служебной программы **dtexec** (dtexec.exe), которая устанавливается с текущим выпуском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], временное обновление пакетов приводит к увеличению времени выполнения. Степень увеличения времени выполнения пакета зависит от размера пакета. Во избежание увеличения времени выполнения рекомендуется обновить пакет перед тем, как запускать его.  
  
|Метод обновления|Тип обновления|  
|--------------------|---------------------|  
|Для запуска пакета [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] используйте служебную программу **dtexec** (dtexec.exe), которая устанавливается с текущим выпуском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Дополнительные сведения см. в статье [dtexec Utility](../packages/dtexec-utility.md).|Результаты обновления пакета являются временными. Для пакета [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] миграция скриптов является временной.<br /><br /> Изменения не могут быть сохранены.|  
|Откройте файл пакета [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|Обновление пакета постоянное, если пакет сохранен; в противном случае временное, если пакет не сохранен.<br /><br /> Для пакетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] миграция скриптов является постоянной, если пакет сохранен; если пакет не сохранен, она является временной.|  
|Добавьте пакет [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] в существующий проект в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|Результаты обновления пакета остаются постоянными. Для пакета [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] постоянной является миграция скриптов.|  
|Откройте файл проекта [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] или [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]и используйте мастер обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , чтобы обновить несколько пакетов в проекте.<br /><br /> Дополнительные сведения см. в разделах [Обновление пакетов служб Integration Services с помощью мастера обновления пакетов служб SSIS](upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md) и [Справка F1 мастера обновления пакетов служб SSIS](../ssis-package-upgrade-wizard-f1-help.md).|Результаты обновления пакета остаются постоянными. Для пакета [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] постоянной является миграция скриптов.|  
|Для запуска пакета <xref:Microsoft.SqlServer.Dts.Runtime.Application.Upgrade%2A> для обновления одного или нескольких пакетов [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|Результаты обновления пакета остаются постоянными. Для пакета [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] постоянной является миграция скриптов.|  
  
## <a name="custom-applications-and-custom-components"></a>Пользовательские приложения и компоненты  
 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] не будут работать с текущим выпуском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Можно использовать последнюю версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] средства для запуска и управления пакетами, которые включают [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] пользовательские компоненты. Были добавлены 4 правила перенаправления привязки к следующим файлам, чтобы помочь перенаправлять сборки среды выполнения от версии 10.0.0.0 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]) до версии 11.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
-   DTExec.exe.config  
  
-   dtshost.exe.config  
  
-   DTSWizard.exe.config  
  
-   DTUtil.exe.config  
  
-   DTExecUI.exe.config  
  
 Чтобы использовать [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] для проектирования пакетов, которые включают [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] настраиваемые компоненты, необходимо изменить файл devenv.exe.config, который находится в каталоге  *\<диска >*: \Program Files\ Microsoft Visual Studio 10.0\Common7\IDE.  
  
 Чтобы эти пакеты работали с клиентскими приложениями, созданными для среды выполнения [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], включите правила переадресации в разделе файла *.exe.config для исполняемого файла. Правила перенаправляют сборки среды выполнения на версию 11.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]). Подробнее о перенаправлении версии сборки см. в разделе [Элемент \<assemblyBinding> для \<runtime>](http://msdn.microsoft.com/library/twy1dw1e.aspx).  
  
### <a name="locating-the-assemblies"></a>Нахождение сборок  
 В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]сборки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] были обновлены до .NET 4.0. Существует отдельный глобальный кэш сборок для .NET 4, который находится в следующем расположении: *\<диск>*:\Windows\Microsoft.NET\assembly. Там вы можете найти все сборки [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , обычно в папке GAC_MSIL.  
  
 Как и в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], путь к основным DLL-файлам расширения [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] имеет вид: *\<диск>*:\Program Files\Microsoft SQL Server\100\SDK\Assemblies.  
  
## <a name="understanding-sql-server-package-upgrade-results"></a>Основные сведения о результатах обновления пакетов SQL Server  
 В процессе обновления пакетов большинство компонентов и функций в пакетах [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] успешно преобразуются в соответствующие объекты из текущего выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако существует несколько компонентов и функций, которые не будут обновлены или на результаты обновления которых следует обратить внимание. В следующей таблице приведены эти компоненты и функции.  
  
> [!NOTE]  
>  Чтобы определить, в каких пакетах возникли неполадки, перечисленные в таблице, запустите помощник по обновлению. Дополнительные сведения см. в разделе [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
|Компонент или функция|Результаты обновления|  
|--------------------------|---------------------|  
|Строки подключения|Для пакетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] изменились имена некоторых поставщиков, из-за чего в строках подключения требуется указывать другие значения. Чтобы обновить строки подключения, выполните одну из следующих процедур.<br /><br /> — Используйте мастер обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], чтобы обновить пакет, и выберите параметр **Обновить строки соединения для использования новых имен поставщиков**.<br /><br /> — В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] на странице "Общие" диалогового окна "Параметры" выберите параметр **Обновить строки соединения для использования новых имен поставщиков**. Дополнительные сведения об этом параметре см. в разделе [General Page](../general-page-of-integration-services-designers-options.md).<br /><br /> — В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] откройте пакет и вручную измените текст свойства ConnectionString.<br /><br /> Примечание: Нельзя применять предыдущие процедуры для обновления строки подключения, если строка подключения хранится в файле конфигурации или файле источника данных, либо в том случае, если выражение устанавливает `ConnectionString` свойство. В таком случае, чтобы обновить строки соединения, необходимо вручную обновить файл конфигурации или выражение.<br /><br /> Дополнительные сведения о доступных источниках данных см. в разделе [Источники данных](../connection-manager/data-sources.md).|  
|Преобразование «Уточняющий запрос»|Для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] пакетов, в процессе обновления автоматически обновляется «Уточняющий запрос» для текущего выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Однако у текущего выпуска этого компонента есть некоторые дополнительные возможности.<br /><br /> Дополнительные сведения см. в статье [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).|  
|Задача «Скрипт» и компонент скрипта|Для пакетов [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] в процессе обновления пакета скрипты из задачи и компонента скрипта автоматически переносятся из VSA в VSTA.<br /><br /> Дополнительные сведения об изменениях, которые может потребоваться внести в скрипт перед выполнением миграции, а также об ошибках их преобразования см. в разделе [Миграция скриптов в VSTA](../../sql-server/install/migrate-scripts-to-vsta.md).|  
  
### <a name="scripts-that-depend-on-adodbdll"></a>Скрипты, зависящие от ADODB.dll  
 Скрипты задачи «Скрипт» и компонента «Скрипт», которые явно ссылаются на файл ADODB.dll, могут не выполняться или не обновляться на компьютерах, на которых не установлена среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] . Чтобы обновить эти скрипты задачи "Скрипт" и компонента скрипта, рекомендуется удалить зависимость от файла ADODB.dll.  Ado.Net — это рекомендуемая альтернатива для такого управляемого кода, как скрипты VB и C#.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Техническая статья [5 советов для беспроблемного обновления служб SSIS до версии SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=235321)на сайте msdn.microsoft.com.  
  
-   Запись в блоге [Использование существующих пользовательских расширений служб SSIS и приложений в Denali](http://go.microsoft.com/fwlink/?LinkId=238157)на blogs.msdn.com.  
  
-   Веб-трансляция [Обновление пакетов служб SSIS в SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=258674)на channel9.msdn.com.  
  
  
