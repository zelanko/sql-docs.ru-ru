---
title: Установка компонентов бизнес-Аналитики SQL Server с SharePoint (PowerPivot и службы Reporting Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 3166107c-30c2-468e-bb1b-bb42b79b37c3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d5088c22fed14e099f77f1ddcc1b7158f9e6f04f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202784"
---
# <a name="install-sql-server-bi-features-with-sharepoint-powerpivot-and-reporting-services"></a>Установка компонентов бизнес-аналитики SQL Server с SharePoint (PowerPivot и службы Reporting Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] может интегрироваться с фермой Microsoft SharePoint для поддержки функций бизнес-аналитики (BI) в SharePoint. Эти функции включают [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] используется для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] доступ к данным на ферме SharePoint. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] — это подсистема обработки данных для книг, созданных в [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel, доступ к которым осуществляется из библиотеки SharePoint. После сохранения [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книгу в SharePoint, можно использовать его как источник данных для [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] отчеты.  
  
 Некоторые действия по установке и настройке, необходимые для SharePoint 2010, отличаются от действий, необходимых для SharePoint 2013. Некоторые подразделы в этом разделе применимы к обеим версиям SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 #124; SharePoint 2010|  
  
 ![Примечание](../../../2014/reporting-services/media/rs-fyinote.png "Примечание") текущие заметки о выпуске, см. в разделе [заметки о выпуске SQL server 2014](http://go.microsoft.com/fwlink/?LinkID=296445).  
  
##  <a name="bkmk_top"></a> В этом разделе  
  
-   [Сценарии бизнес-Аналитики SQL Server и SharePoint 2013](#bkmk_bi_scenarios)  
  
-   [Общие сведения об установке](#bkmk_install_sharepoint2013_overview)  
  
## <a name="in-this-section"></a>в этом разделе  
 В дополнение к сведениям в этом разделе см. следующие темы также в этом разделе содержимого.  
  
 [Топологии развертывания для компонентов бизнес-аналитики SQL Server в SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)  
  
 [Указания по использованию функций бизнес-аналитики SQL Server в ферме SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
 [Контрольные списки для установки компонентов бизнес-аналитики в SharePoint](../../../2014/sql-server/install/checklists-for-installing-bi-features-with-sharepoint.md)  
  
 [Установку в режиме интеграции с SharePoint служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  
  
 [Установка PowerPivot для SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
##  <a name="bkmk_bi_scenarios"></a> Сценарии бизнес-Аналитики SQL Server и SharePoint 2013  
 В этом разделе представлены различные уровни бизнес-аналитики, которые можно установить и настроить.  
  
 Службы Excel в SharePoint 2013 включают функции модели данных для обеспечения взаимодействия с книгой [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в браузере. Для базовых функций модели данных не нужно развертывать [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] надстройка 2013 в ферме. Достаточно установить сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint и зарегистрировать сервер в параметрах **Модель данных** служб Excel.  
  
 Развертывание [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] надстройка 2013 задействовать дополнительные функции и компоненты в ферме SharePoint. Дополнительные возможности включают [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] коллекции, обновления данных расписания и панели управления PowerPivot. Дополнительные сведения см. в таблице.  
  
||Level|Компоненты|Установка и настройка|  
|-|-----------|--------------|--------------------------|  
|1|Только SharePoint|Собственные функции служб Excel|Службы Excel и другие службы, поставляемые с SharePoint Server 2013.|  
|**2**|SharePoint со службами Analysis Services в режиме интеграции с SharePoint|Интерактивные книги PowerPivot в браузере|Установите [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint.<br /><br /> Зарегистрируйте сервер служб Analysis Services в службах Excel.|  
|**3**|SharePoint со службами Reporting Services в режиме интеграции с SharePoint|Power View|Установите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.<br /><br /> Установка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройки **(rsSharePoint.msi)** для SharePoint. Дополнительные сведения см. в разделе [Установка или удаление надстройки служб Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)|  
|**4**|Все функции PowerPivot|Доступ к книгам для использования их в качестве источника данных из-за пределов фермы.<br /><br /> Расписание обновления данных.<br /><br /> Коллекция PowerPivot.<br /><br /> Панель мониторинга управления.<br /><br /> Тип содержимого файла связи BISM.|Развертывание PowerPivot для надстройки SharePoint 2013 **(spPowerPivot.msi)**. Дополнительные сведения см. в следующих разделах:<br /><br /> [Установка или удаление PowerPivot для SharePoint надстройка &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)<br /><br /> Дополнительные сведения о том, как загрузить **spPowerPivot.msi**, см. в разделе [Загрузка SQL Server 2014 PowerPivot для SharePoint](http://go.microsoft.com/fwlink/?LinkID=296473).|  
  
 Дополнительные сведения о включении [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] функции, см. в разделе [The Light-Up истории бизнес-Аналитики SQL Server для SharePoint 2013](http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx) (http://blogs.msdn.com/b/analysisservices/archive/2012/07/27/introducing-the-bi-light-up-story-for-sharepoint-2013.aspx).  
  
##  <a name="bkmk_install_sharepoint2013_overview"></a> Общие сведения об установке  
 Если вы хотите использовать оба метода [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], дважды запустить мастер установки SQL Server. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] можно выбрать отдельно на **роль установки** страницы мастера установки SQL Server.  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] поддерживает SharePoint 2010 и SharePoint 2013; Тем не менее в зависимости от версии SharePoint используются различные архитектуры и процесс установки.  
  
 Ниже приводится сводка шагов установки для развертывания компонентов бизнес-аналитики [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на одиночном сервере.  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013**  
  
 Для **SharePoint 2013**, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] возможность установки на сервере, который не имеет установленного продукта SharePoint. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Архитектура, используемая для SharePoint 2013, выполняется **за пределами** фермы SharePoint и может быть установлена на сервере, который содержит установку SharePoint, или он может быть установлен на сервере, не содержит Установка SharePoint.  
  
1.  Установите SharePoint Server 2013 и включите службы Excel.  
  
2.  Установите службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции фермы SharePoint и предоставьте учетным записям службы и ферме права администратора в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Для обеих версий SharePoint [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] процесс установки начинается с выбора установки роли **SQL Server PowerPivot для SharePoint** в мастере установки SQL Server или с использованием командной строки SQL Server Установка.  
  
     ![Роль установки](../../../2014/sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "роль установки")  
  
3.  Для SharePoint 2013, вы можете расширить [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] функции и процедуру взаимодействия. Скачайте и запустите **spPowerPivot.msi** серверных данных обновления обработки, совместной работы и управления поддержки для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книги. Дополнительные сведения см. в разделе [Microsoft SQL Server 2014 PowerPivot для Microsoft® SharePoint](http://go.microsoft.com/fwlink/?LinkID=324854).  
  
     Запустите [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] пакет установки 2013 **spPowerPivot.msi** поставщики устанавливаются на каждом сервере в ферме SharePoint, чтобы обеспечить правильную версию данных.  
  
4.  Чтобы настроить [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2013 используйте **PowerPivot для SharePoint 2013** средство.  
  
     Мастер установки SQL Server устанавливает два [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] средства настройки. Одно из средств настройки поддерживает SharePoint 2013, а другое — SharePoint 2010.  
  
     ![два средства настройки powerpivot](../../../2014/analysis-services/media/as-powerpivot-configtools-bothicons.gif "два средства настройки powerpivot")  
  
5.  Настройте службы Excel в SharePoint Server 2013 для использования экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Дополнительные сведения см. раздел «Настройка базовой Analysis Services интеграции SharePoint» в [установки PowerPivot для SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)и [параметрами (SharePoint Server модели управление данных служб Excel 2013)](http://technet.microsoft.com/library/jj219780.aspx) (http://technet.microsoft.com/library/jj219780.aspx).  
  
6.  Дополнительные сведения см. в разделе [установки PowerPivot для SharePoint 2013](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
 **[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010**  
  
 Для SharePoint 2010 необходимо выполнять установку [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint на сервере, на котором уже установлен или будет установлен SharePoint 2010. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Архитектуры для SharePoint 2010 выполняется **внутри** фермы и требует SharePoint на сервере, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint должен быть установлен.  
  
1.  Установите службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции фермы SharePoint и предоставьте учетным записям службы и ферме права администратора в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Развертывание SharePoint 2010 не поддерживает файл spPowerPivot.msi, и MSI-файл **не требуется** для SharePoint 2010.  
  
     Для обеих версий SharePoint [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] процесс установки начинается с выбора установки роли **SQL Server PowerPivot для SharePoint** в мастере установки SQL Server или с использованием командной строки SQL Server Установка.  
  
2.  Мастер установки SQL Server устанавливает два [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] средства настройки. Одно из средств настройки поддерживает SharePoint 2013, а другое — SharePoint 2010.  
  
     Чтобы настроить [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2010 используйте **средство настройки PowerPivot** .  
  
3.  Дополнительные сведения см. в разделе [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**  для SharePoint 2010 и 2013  
  
1.  Установка для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint — изменились по сравнению с предыдущим выпуском.  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Шаги установки для SharePoint 2010 и SharePoint 2013 очень похожи. Важные замечания о версиях SharePoint:  
  
    -   См. поддерживаемые сочетания из следующих:  
  
        -   Версия служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
        -   Надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint.  
  
        -   Версия продукта SharePoint.  
  
         [Поддерживаемые сочетания SharePoint и компонентов служб Reporting Services и надстройки &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
    -   Для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в SharePoint 2010 требуется SharePoint 2010 с пакетом обновления 2 (SP2).  
  
    1.  Установите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. [Установку в режиме интеграции с SharePoint служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41; ](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md) и [Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
    2.  Установите надстройку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint (rsSharePoint.msi). См. в разделе [Установка или удаление Reporting Services надстройки для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Для текущей версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] надстройка для SharePoint, см. в разделе [где найти надстройку служб Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
    3.  Настройка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] службы SharePoint и по крайней мере один [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] приложения службы. Дополнительные сведения см. раздел «Создание отчетов служб приложения службы» в [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
  
##  <a name="bkm_database_attach"></a> Общие сведения о присоединением базы данных обновления и SharePoint 2013  
 SharePoint 2013 не поддерживает обновление на месте. Однако **обновление присоединением базы данных поддерживается**.  
  
 Если имеется экземпляр PowerPivot, интегрированный с SharePoint 2010, невозможно выполнить обновление на месте сервера SharePoint.  Однако можно выполнить следующие действия в процессе обновления присоединением базы данных SharePoint.  
  
1.  Установка новой фермы SharePoint Server 2013  
  
2.  Выполните обновление присоединением базы данных SharePoint и перенесите связанные с PowerPivot базы данных содержимого в ферму SharePoint 2013.  
  
3.  Установка экземпляра SQL Server Analysis Services в режиме интеграции с SharePoint и предоставьте учетным записям фермы и служб SharePoint, права администратора сервера в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
4.  Установите пакет установки PowerPivot для SharePoint 2013 **spPowerPivot.msi** на каждом сервере в ферме SharePoint.  
  
5.  В центре администрирования SharePoint 2013 настройте службы Excel для использования сервера служб Analysis Services в режиме интеграции с SharePoint, созданном на шаге 3.  
  
     Для переноса расписаний обновления настройте приложение службы PowerPivot.  
  
> [!NOTE]  
>  Дополнительные сведения об обновлении присоединением базы данных PowerPivot и SharePoint см. в следующих разделах:  
  
-   [Перенос PowerPivot на SharePoint 2013](../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)  
  
-   [Общие сведения о процессе обновления до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Подготовка с очисткой перед обновлением до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256689).  
  
-   [Обновление баз данных с SharePoint 2010 до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
## <a name="see-also"></a>См. также  
 [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Поддерживаемые сочетания SharePoint и компонентов служб Reporting Services и надстройки &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)   
 [Установка или удаление Reporting Services надстройки для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
