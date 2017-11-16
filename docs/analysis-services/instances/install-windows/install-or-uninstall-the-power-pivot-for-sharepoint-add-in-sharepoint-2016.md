---
title: "Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2016) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34dd07b8-d59d-49ce-bad0-74f40e4db0b8
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1dbd22c1c09de66200cda7300f34666ea453777a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2016"></a>Установка или удаление надстройки Power Pivot для SharePoint (SharePoint 2016)
  [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] представляет собой набор компонентов сервера приложений и служб, которые обеспечивают доступ к данным [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в ферме [!INCLUDE[SPS2016](../../../includes/sps2016-md.md)] . Надстройка [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint (**spPowerpivot16.msi**) — это пакет установщика, используемый для установки компонентов сервера приложений.  
  
 **Примечание.** В этой статье описывается установка файлов решений [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и средства настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2016. После установки сведения о средстве настройки и дополнительных компонентах см. в разделе [Настройка PowerPivot и развертывание решений (SharePoint 2013)](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md).  
  
 Дополнительные сведения о том, как загрузить **spPowerPivot16.msi**, см. в документации по [Microsoft® SQL Server® 2016 Power Pivot® для Microsoft SharePoint®](https://www.microsoft.com/download/details.aspx?id=52675).  
  
 **В этом разделе:**  
  
-   [Историческая справка](#bkmk_background)  
  
-   [Куда устанавливать spPowerPivot16.msi?](#bkmk_where_to_install)  
  
-   [Требования и необходимые условия](#bkmk_prereq)  
  
-   [Установка Power Pivot для SharePoint](#bkmk_install)  
  
-   [Развертывание файлов решения SharePoint с помощью средства настройки Power Pivot для SharePoint 2016](#bkmk_deploy_solution)  
  
-   [Удаление или восстановление надстройки](#bkmk_remove_addin)  
  

**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2016 
  
##  <a name="bkmk_background"></a> Историческая справка  
  
-   **Сервер приложений:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в SharePoint 2016 имеются возможности использования рабочих книг в качестве источников данных, возможности запланированного обновления данных и панель мониторинга управления [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
     [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] — пакет установщика [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows (**spPowerpivot16.msi**), который развертывает клиентские библиотеки служб Analysis Services и копирует файлы установки [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] на компьютер. Установщик не разворачивает и не настраивает функции [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в SharePoint. По умолчанию устанавливаются следующие компоненты:  
  
    -   [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)]. Этот компонент содержит скрипты PowerShell (PS1-файлы), пакеты решения SharePoint (WSP-файлы) и средство настройки [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] для развертывания [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в ферме SharePoint 2016.  
  
    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Поставщик OLE DB для служб Analysis Services (MSOLAP).  
  
    -   Поставщик данных ADOMD.NET.  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Объекты управления аналитикой (AMO-объекты).  
  
-   **Серверные службы.** Если вы создаете книги с аналитическими данными с помощью [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel, то для доступа к этим данным в серверной среде потребуется настроить связку Office Online Server с сервером бизнес-аналитики, на котором запущена служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в режиме [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Вы можете запустить программу установки SQL Server на компьютере, где установлено решение SharePoint Server 2016, или на другом компьютере без ПО SharePoint. Службы Analysis services нисколько не зависят от SharePoint.  
  
     Дополнительные сведения об установке, отмене установки и настройке серверных служб см. в следующем документе:  
  
    -   [Установка служб Analysis Services в режиме Power Pivot](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
    -   [Удаление Power Pivot для SharePoint](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
##  <a name="bkmk_where_to_install"></a> Куда устанавливать spPowerPivot16.msi?  
 Мы рекомендуем устанавливать **spPowerPivot16.msi** на всех серверах фермы SharePoint, чтобы обеспечить согласованность конфигурации, в том числе на серверах приложений и серверах веб-интерфейса. В пакет установщика входят поставщики данных служб Analysis Services, а также средство настройки [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] . При установке **spPowerPivot16.msi** вы можете исключить определенные компоненты.  
  
 **Поставщики данных.** Некоторые технологии SharePoint и SQL Server используют поставщики данных служб Analysis Services, включая службы PerformancePoint и Power View. Установка **spPowerPivot16.msi** на всех серверах SharePoint обеспечивает полный набор поставщиков данных служб Analysis Services, а также постоянную возможность подключения к [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в ферме.  
  
> [!NOTE]  
>  Поставщики данных служб Analysis Services на сервере SharePoint 2016 следует устанавливать с помощью **spPowerPivot16.msi**. Другие пакеты установщика, доступные в составе пакета дополнительных компонентов [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , не поддерживаются, так как они не содержат файлы поддержки SharePoint 2016, которые требуются поставщикам данных для этой среды.  
  
 **Средство настройки.** Средство настройки [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] требуется только на одном из серверов SharePoint. Однако в многосерверных фермах рекомендуется устанавливать средство настройки по крайней мере на 2 сервера, чтобы обеспечить доступ к средству настройки, даже если один из двух серверов находится вне сети.  
  
##  <a name="bkmk_prereq"></a> Требования и необходимые условия  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SharePoint Server 2016.  
  
-   **spPowerPivot16.msi** подходит только для 64-разрядной версии (в соответствии с требованиями к продуктам и технологиям SharePoint).  
  
-   Сервер в [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] режиме. Office Online Server будет использовать экземпляр служб SQL Server Analysis Services в качестве сервера [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Службы Analysis Services могут работать на локальном сервере SharePoint или на удаленном компьютере. Эти службы нельзя установить на сервер Office Online Server.  
  
-   **Разрешения.** Чтобы установить [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)], текущий пользователь должен иметь права администратора на этом компьютере и быть членом группы администраторов фермы SharePoint.  
  
-   Дополнительные сведения о требованиях и необходимых условиях для [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] см. в разделе [Требования к оборудованию и программному обеспечению для сервера служб Analysis Services в режиме интеграции с SharePoint](http://msdn.microsoft.com/library/fb86ca0a-518c-4c61-ae78-7680c57fae1f).  
  
##  <a name="bkmk_install"></a> Установка Power Pivot для SharePoint  
 Пакет установщика **spPowerpivot16.msi** поддерживает как графический пользовательский интерфейс, так и режим командной строки. При использовании этих методов установки необходимо запустить MSI-файл с правами администратора. После установки сведения о средстве настройки и дополнительных компонентах см. в разделе [Настройка PowerPivot и развертывание решений (SharePoint 2013)](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md).  
  
### <a name="user-interface-installation"></a>Установка с помощью пользовательского интерфейса  
 Чтобы установить [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] с помощью графического пользовательского интерфейса, выполните следующие шаги.  
  
1.  Запустите **spPowerPivot16.msi**.  
  
2.  На странице приветствия нажмите кнопку **Далее** .  
  
3.  Прочитайте и примите лицензионное соглашение, затем нажмите кнопку **Далее**.  
  
4.  На странице **Выбор компонентов** все компоненты выбраны по умолчанию.  
  
5.  Выберите **Далее**.  
  
6.  Нажмите **Установить** , чтобы завершить установку.  
  
### <a name="command-line-installation"></a>Установка из командной строки  
 Для установки из командной строки откройте командную строку с правами администратора, а затем запустите файл **spPowerPivot16.msi**. Например:  
  
 `Msiexec.exe /i spPowerPivot16.msi`.  
  
 Чтобы создать журнал установки, можно использовать стандартные переключатели ведения журнала MsiExec. В следующем примере создается файл журнала «Install_Log.txt» с помощью переключателя подробного ведения журнала «v».  
  
```  
Msiexec.exe /i spPowerPivot16.msi /L v c:\test\Install_Log.txt  
```  
  
### <a name="quiet-command-line-installation-for-scripting"></a>Автоматическая установка из командной строки для создания скрипта  
 Вы можете использовать переключатели **/q** или **/quiet** для автоматической установки, в ходе которой не будут выводиться никакие диалоговые окна или сообщения. Автоматическая установка удобна, если установку надстройки нужно выполнить из скрипта.  
  
> [!IMPORTANT]  
>  При использовании параметра **/q** для автоматической установки из командной строки условия лицензионного соглашения не отображаются. Независимо от метода установки, использование программного обеспечения регулируется лицензионным соглашением и пользователь несет ответственность за его соблюдение.  
  
 **Выполнение автоматической установки**  
  
1.  Откройте командную строку **с разрешениями администратора**.  
  
2.  Выполните следующую команду:  
  
    ```  
    Msiexec.exe /i spPowerPivot16.msi /q  
    ```  
  
### <a name="command-line-installation-to-include-specific-components"></a>Установка из командной строки для включения определенных компонентов  
 Нет необходимости в средстве настройки [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] на каждом сервере SharePoint, однако рекомендуется установить этот компонент как минимум на двух серверах, чтобы он был доступен в нужный момент.  
  
 При установке spPowerPivot16.msi вы можете использовать параметры командной строки для выбора конкретных элементов, например установить только поставщиков данных, но не средство настройки [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] . Следующая командная строка представляет собой пример установки всех компонентов, кроме средства настройки.  
  
```  
Msiexec /i spPowerPivot16.msi AGREETOLICENSE="yes" ADDLOCAL=” SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common”  
```  
  
|Параметр|Описание|  
|------------|-----------------|  
|Analysis_Server_SP_addin16|[!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] Конфигурация|  
|SQL_OLAPDM|Поставщик OLE DB служб Analysis Services для SQL Server 2016|  
|SQL_ADOMD|Поставщик ADOMD.NET|  
|SQL_AMO|Поставщик объектов SQL Server 2016 AMO|  
|SQLAS_SP16_Common|Общие компоненты служб Analysis Services для SharePoint 2016|  
  
##  <a name="bkmk_deploy_solution"></a> Развертывание файлов решения SharePoint с помощью средства настройки Power Pivot для SharePoint 2016  
 Среди файлов, которые программа spPowerPivot16.msi скопирует на жесткий диск, три являются файлами решения SharePoint. Область одного файла решения — уровень фермы, а область другого файла — уровень веб-приложения. Это относится к следующим файлам:  
  
-   `PowerPivot16FarmSolution.wsp`  

-   `PowerPivot16WebApplicationSolution.wsp`  
  
 Файлы решений копируются в следующую папку:  
  
 `ssInstallPathTools\PowerPivotTools\SPAddinConfiguration\Resources`  
  
 После установки MSI-файла запустите средство настройки [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] для настройки и развертывания решений в ферме SharePoint.  
  
 **Для запуска средства настройки выполните следующие действия.**  
  
 На экране "Пуск" в Windows введите "power" и в результатах поиска приложений щелкните **Настройка [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)]**. Обратите внимание, что результаты поиска могут включать две ссылки, так как программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливает отдельные средства настройки служб [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2013 и SharePoint 2016. Убедитесь, что вы запускаете средство настройки [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] .  
  
 ![Настройка PowerPivot для SharePoint 2016](../../../analysis-services/instances/install-windows/media/powerpivot-for-sharepoint-2016-configuration.png "PowerPivot для SharePoint 2016")  
  
 **Or**  
  
1.  Откройте меню **Пуск**, **Все программы**.  
  
2.  Выберите [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)].  
  
3.  Щелкните **Средства настройки**.  
  
4.  На странице приветствия нажмите кнопку **[!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] Конфигурация**.  
  
 Дополнительные сведения о средстве настройки см. в разделе [Power Pivot Configuration Tools](../../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
##  <a name="bkmk_remove_addin"></a> Удаление или восстановление надстройки  
  
> [!CAUTION]  
>  При удалении **spPowerPivot16.msi** удаляются поставщики данных и средства настройки. После удаления поставщиков данных сервер не сможет подключиться к [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)].  
  
 Удалить или восстановить [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] вы можете одним из следующих способов.  
  
1.  **На панели управления Windows** . Выберите [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]**[!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)]**. Щелкните **Удалить** или **Восстановить**.  
  
2.  Запустите spPowerPivot16.msi и выберите вариант **Удалить** или **Восстановить** .  
  
 **Из командной строки.** Чтобы восстановить или удалить [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] из командной строки, откройте окно командной строки **с правами администратора** и выполните одну из следующих команд.  
  
-   Для восстановления выполните следующую команду:  
  
    ```  
    msiexec.exe /f spPowerPivot16.msi  
    ```  
  
 или  
  
-   Для удаления выполните следующую команду:  
  
    ```  
    msiexec.exe /uninstall spPowerPivot16.msi  
    ```  
  
  

