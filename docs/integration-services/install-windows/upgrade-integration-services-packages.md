---
title: Обновление пакетов служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, migrating
- migrating packages [Integration Services]
ms.assetid: 68dbdf81-032c-4a73-99f6-41420e053980
author: MikeRayMSFT
ms.author: mikeray
manager: erikre
ms.openlocfilehash: 3d458e7696719c383b03a5cc3f259de08e4b8c37
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68262782"
---
# <a name="upgrade-integration-services-packages"></a>Обновление пакетов служб Integration Services

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  При обновлении экземпляра [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до текущего выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]существующие пакеты [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] не будут автоматически обновлены до формата пакетов, используемого в текущем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Необходимо будет выбрать метод обновления и обновить эти пакеты вручную.  
  
 Сведения об обновлении пакетов при преобразовании проекта в модель развертывания проекта см. в разделе [Развертывание проектов на сервере Integration Services](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)
  
## <a name="selecting-an-upgrade-method"></a>Выбор метода обновления  
 Можно использовать различные методы обновления пакетов [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] . Для некоторых из этих методов обновление лишь временное. Для других — обновление постоянное. В следующей таблице описан каждый из этих методов и указано, является обновление временным или постоянным.  
  
> [!NOTE]  
>  При запуске пакета [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с помощью служебной программы **dtexec** (dtexec.exe), которая устанавливается с текущим выпуском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], временное обновление пакетов приводит к увеличению времени выполнения. Степень увеличения времени выполнения пакета зависит от размера пакета. Во избежание увеличения времени выполнения рекомендуется обновить пакет перед тем, как запускать его.  
  
|Метод обновления|Тип обновления|  
|--------------------|---------------------|  
|Для запуска пакета **,** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]используйте служебную программу [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]dtexec [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)](dtexec.exe), которая устанавливается с текущим выпуском [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] .<br /><br /> Дополнительные сведения см. в статье [dtexec Utility](../../integration-services/packages/dtexec-utility.md).|Результаты обновления пакета являются временными.<br /><br /> Изменения не могут быть сохранены.|  
|Откройте файл пакета [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|Обновление пакета постоянное, если пакет сохранен; в противном случае временное, если пакет не сохранен.|  
|Добавьте пакет [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] в существующий проект в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|Результаты обновления пакета остаются постоянными.|  
|Откройте файл проекта [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] или более поздней версии в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]и используйте мастер обновления пакетов [!INCLUDE[ssIS](../../includes/ssis-md.md)] , чтобы обновить несколько пакетов в проекте.<br /><br /> Дополнительные сведения см. в разделах [Обновление пакетов служб Integration Services с помощью мастера обновления пакетов служб SSIS](../../integration-services/install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md) и [Справка F1 мастера обновления пакетов служб SSIS](../../integration-services/ssis-package-upgrade-wizard-f1-help.md).|Результаты обновления пакета остаются постоянными.|  
|Для запуска пакета <xref:Microsoft.SqlServer.Dts.Runtime.Application.Upgrade%2A> для обновления одного или нескольких пакетов [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|Результаты обновления пакета остаются постоянными.|  
  
## <a name="custom-applications-and-custom-components"></a>Пользовательские приложения и компоненты  
 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] не будут работать с текущим выпуском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 С помощью текущего выпуска инструментов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно запускать пакеты, содержащие пользовательские компоненты [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssIS](../../includes/ssis-md.md)] , и управлять ими. Мы добавили четыре правила перенаправления привязки к следующим файлам, чтобы помочь перенаправлять сборки среды выполнения от версии 10.0.0.0 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 11.0.0.0 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) или 12.0.0.0 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) к версии 13.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
-   DTExec.exe.config  
  
-   dtshost.exe.config  
  
-   DTSWizard.exe.config  
  
-   DTUtil.exe.config  
  
-   DTExecUI.exe.config  
  
 Чтобы проектировать в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] пакеты, в состав которых входят пользовательские компоненты [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], необходимо внести изменения в файл devenv.exe.config, который находится в каталоге *\<диск>* :\Program Files\Microsoft Visual Studio 10.0\Common7\IDE.  
  
 Чтобы эти пакеты работали с клиентскими приложениями, созданными для среды выполнения [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], включите правила переадресации в разделе файла *.exe.config для исполняемого файла. Правила перенаправляют сборки среды выполнения к версии 13.0.0.0 ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]). Подробнее о перенаправлении версии сборки см. в разделе [Элемент \<assemblyBinding> для \<runtime>](https://msdn.microsoft.com/library/twy1dw1e.aspx).  
  
### <a name="locating-the-assemblies"></a>Нахождение сборок  
 В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]сборки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] были обновлены до .NET 4.0. Существует отдельный глобальный кэш сборок для .NET 4, который находится в следующем расположении: *\<диск>* :\Windows\Microsoft.NET\assembly. Там вы можете найти все сборки [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , обычно в папке GAC_MSIL.  
  
 Как и в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], путь к основным DLL-файлам расширения [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] имеет вид: *\<диск>* :\Program Files\Microsoft SQL Server\130\SDK\Assemblies.  
  
## <a name="understanding-sql-server-package-upgrade-results"></a>Основные сведения о результатах обновления пакетов SQL Server  
 В процессе обновления пакетов большинство компонентов и функций в пакетах [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] успешно преобразуются в соответствующие объекты в текущем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако существует несколько компонентов и функций, которые не будут обновлены или на результаты обновления которых следует обратить внимание. В следующей таблице приведены эти компоненты и функции.  
  
> [!NOTE]  
>  Чтобы определить, в каких пакетах возникли неполадки, перечисленные в таблице, запустите помощник по обновлению.  
  
|Компонент или функция|Результаты обновления|  
|--------------------------|---------------------|  
|Строки подключения|Для пакетов [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]и [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] изменились имена некоторых поставщиков, из-за чего в строках подключения требуется указывать другие значения. Чтобы обновить строки подключения, выполните одну из следующих процедур.<br /><br /> Используйте мастер обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , чтобы обновить пакет, и выберите параметр **Обновить строки соединения для использования новых имен поставщиков** .<br /><br /> В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]на странице «Общие» диалогового окна «Параметры» выберите параметр **Обновление строк соединения для использования новых имен поставщиков** . Дополнительные сведения об этом параметре см. в разделе "Страница "Общие"".<br /><br /> В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет и вручную измените текст свойства ConnectionString.<br /><br /> Примечание. Нельзя применять предыдущие процедуры для обновления строки подключения, если она хранится в файле конфигурации или файле источника данных либо если выражение устанавливает свойство **ConnectionString** . В таком случае, чтобы обновить строки соединения, необходимо вручную обновить файл конфигурации или выражение.<br /><br /> Дополнительные сведения о доступных источниках данных см. в разделе [Источники данных](../../integration-services/connection-manager/data-sources.md).|  
  
### <a name="scripts-that-depend-on-adodbdll"></a>Скрипты, зависящие от ADODB.dll  
 Скрипты задачи «Скрипт» и компонента «Скрипт», которые явно ссылаются на файл ADODB.dll, могут не выполняться или не обновляться на компьютерах, на которых не установлена среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] . Чтобы обновить эти скрипты задачи "Скрипт" и компонента скрипта, рекомендуется удалить зависимость от файла ADODB.dll.  Ado.Net — это рекомендуемая альтернатива для такого управляемого кода, как скрипты VB и C#.  
  
  
