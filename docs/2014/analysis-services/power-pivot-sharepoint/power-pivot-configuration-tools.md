---
title: Средства настройки PowerPivot | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f934c51d-01fe-4e67-971d-cd87d7d7ee51
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e2803d0bb8d4ed506208a3dff577e25ec891d6e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317014"
---
# <a name="powerpivot-configuration-tools"></a>PowerPivot Configuration Tools
  Настройка, исправление или удаление [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] с помощью средств настройки PowerPivot.  
  
 Мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] установит средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2010, а также средство настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2013. В этом разделе приводится описание принципов использования обоих средств и различий между ними.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010  
  
 **В этом разделе.**  
  
-   [Требования к использованию средств настройки](#bkmk_requirements)  
  
-   [2 версии средства настройки](#bkmk_twoversions)  
  
-   [Общие сведения об использовании средства настройки PowerPivot](#bkmk_overview)  
  
-   [Запуск одного из средств настройки PowerPivot](#bmkm_start_tool)  
  
##  <a name="bkmk_requirements"></a> Требования к использованию средств настройки  
  
-   Необходимо быть администратором фермы.  
  
-   Необходимо быть администратором сервера для экземпляра служб Analysis Services (только для SharePoint 2010).  
  
-   Необходимо быть членом роли db_owner в базе данных конфигурации фермы.  
  
-   При работе со средствами настройки порты TCP/IP не задействуются, поэтому не нужно выполнять какую-либо особую настройку брандмауэра. При работе со средством настройки подразумевается, что веб-приложения и общие службы входят в состав платформы SharePoint. Может потребоваться настройка брандмауэра для сервера служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в статье [Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
##  <a name="bkmk_twoversions"></a> 2 версии средства настройки  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Мастер установки устанавливает средство настройки PowerPivot для SharePoint 2010, а также средство настройки PowerPivot для SharePoint 2013.  
  
 Средства можно использовать только с экземпляром [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] объекта [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Не следует использовать средства с установками [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .  
  
|Имя|Поддерживаемая версия SharePoint|Подробные данные конфигурации|  
|----------|-------------------------------------|----------------------------|  
|Настройка PowerPivot для SharePoint 2013|SharePoint 2013|[Настройка или восстановление PowerPivot для SharePoint 2013 &#40;средство настройки PowerPivot&#41;](configure-or-repair-power-pivot-for-sharepoint-2013.md)|  
|Средство настройки PowerPivot|SharePoint 2010 с @@@SharePoint 2010@@@|[Настройка или восстановление PowerPivot для SharePoint 2010 &#40;средство настройки PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md)|  
  
###  <a name="bkmk_sum_differences_betweentools"></a> Отличия двух средств настройки  
 Две версии средств настройки похожи, однако есть отличия в этапах настройки, которые применяются средствами. Отличия обусловлены изменениями между SharePoint 2010 и SharePoint 2013, а также отличиями в архитектуре между версией SQL Server 2012 с пакетом обновления 1 (SP1) PowerPivot для SharePoint и предыдущими версиями PowerPivot для SharePoint.  
  
 В следующей таблице приводится описание новых и измененных функций в средстве **Настройка PowerPivot для SharePoint 2013** . Таблица также содержит описание возможностей в **средстве настройки PowerPivot** , не входящих в средство настройки PowerPivot для SharePont 2013. Строки в таблице располагаются в том же порядке, что и вкладки в средстве настройки.  
  
|Настройка PowerPivot для SharePoint 2013|Средство настройки PowerPivot|  
|--------------------------------------------------|-----------------------------------|  
|На главной странице появился новый параметр для **PowerPivot Server для служб Excel**. Параметр поддерживает новую архитектуру с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , выполняемым за пределами фермы SharePoint. Необходимо настроить службы Excel для использования одного или нескольких серверов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , работающих в режиме интеграции с SharePoint.<br /><br /> ![Сервер PowerPivot в новом средстве настройки](../media/as-powerpivot-configtool-differences-new-mainpage.gif "сервера PowerPivot в новом средстве настройки")||  
||Средство 2010 содержит страницу **регистрация служб SQL Server Analysis Services (PowerPivot) на локальном сервере** для настройки локального экземпляра [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Эта страница не является частью средства 2013, поскольку локальный экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]отсутствует.<br /><br /> ![КАК учетная запись службы в старом средстве настройки](../media/as-powerpivot-configtool-differences-old-register-as-localserver.gif "как учетная запись службы в старом средстве настройки")|  
||Страница **Создание приложения службы PowerPivot** содержит дополнительный параметр **Обновить книги, чтобы получить возможность обновления данных**. Этот параметр недоступен в средстве 2013.<br /><br /> ![Обновление книг в старом средстве настройки](../media/as-powerpivot-configtool-differences-old-uprgadeworkbooks.gif "обновление книг в старом средстве настройки")|  
|В средстве 2013 появилась новая страница **Настройка серверов PowerPivot**. Эта страница поддерживает новую архитектуру экземпляра [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , выполняемого за пределами фермы SharePoint. По умолчанию имя сервера, которое было указано на главной странице в текстовом поле **Сервер PowerPivot для служб Excel**, также отображается на вкладке **Настройка серверов PowerPivot**.<br /><br /> ![Зарегистрировать новое средство настройки PowerPivot сервера](../media/as-powerpivot-configtool-differences-new-powerpivot-servers.gif "новое средство настройки PowerPivot для регистрации сервера")||  
|В средстве 2013 появилась новая страница **Регистрация надстройки PowerPivot в качестве модуля отслеживания служб Excel**. Службы Excel services SharePoint 2010 не отслеживают сведения об использовании PowerPivot.||  
||Средство 2010 содержит страницу **Добавить MSOLAP.5 в качестве доверенного поставщика** для регистрации MSOLAP, чтобы службы Excel могли загружать в SharePoint 2010 модели PowerPivot. Эта страница не является частью средства 2013. SharePoint 2013 со службами Excel не использует поставщика MSOLAP для моделей загрузки.|  
  
##  <a name="bkmk_overview"></a> Общие сведения об использовании средства настройки PowerPivot  
 При запуске одного из средств настройки PowerPivot средство оценивает существующую установку для определения применимых операций. Для новой установки доступна только задача настройки. После настройки сервера появляется задача удаления. Если исходной установкой является экземпляр [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] , в списке доступных задач появится обновление.  
  
 При отсутствии навыков работы с центром администрирования или Windows PowerShell это средство настройки можно использовать как альтернативу указанным инструментам для установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .  
  
 Кроме того, средство умеет определять, настроена ли ферма, и не отсутствуют ли необходимые компоненты. Если программные файлы SharePoint установлены, но ферма не настроена, средство предоставляет действия для настройки фермы и установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .  
  
 Ознакомьтесь с вкладкой **Скрипт** , чтобы изучить возможности настройки PowerPivot и SharePoint с помощью Windows PowerShell. Дополнительные сведения см. в следующих разделах:  
  
-   [Настройка PowerPivot с помощью Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
-   [Справочник по PowerShell для PowerPivot для SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
> [!NOTE]  
>  Средство не настраивает службы Reporting Services. При добавлении служб Reporting Services в среду SharePoint их следует устанавливать и настраивать отдельно. Дополнительные сведения см. в следующих разделах:  
>   
>  -   [Установка служб Reporting Services в режиме SharePoint для SharePoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).  
> -   [Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
##  <a name="bmkm_start_tool"></a> Запуск одного из средств настройки PowerPivot  
  
1.  На **запустить** введите `powerpivot`  
  
     На **запустить** введите `powerpivot` или на **запустить** меню, щелкните **все программы**, нажмите кнопку [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], нажмите кнопку **средства настройки** , а затем выберите один из следующих:  
  
    -   **Средство настройки PowerPivot**.  
  
    -   **OR**  
  
    -   **Настройка PowerPivot для SharePoint 2013**.  
  
     ![два средства настройки powerpivot](../media/as-powerpivot-configtools-bothicons.gif "два средства настройки powerpivot")  
  
     **Примечание.** Эти средства доступны, только если на локальном сервере установлен компонент [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] .  
  
2.  Во время запуска средство настройки проверяет состояние установки и предоставляет задачи, допустимые для нее.  
  
3.  В зависимости от текущего состояния установки можно выполнить одну или несколько задач, указанных далее.  
  
    1.  Нажмите кнопку **Настройка или восстановление PowerPivot для SharePoint** для выполнения задач после установки или для восстановления установки.  
  
    2.  Нажмите кнопку **Удаление компонентов, служб, приложений и решений** для удаления компонентов и решений с фермы.  
  
    3.  Нажмите кнопку **Обновление компонентов, служб, приложений и решений** для обновления компонентов и решений, установленных с помощью предыдущей версии [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].  
  
     Например, изображение показывает страницу запуска средства настройки PowerPivot для SharePoint 2013.  
  
     ![Средство PowerPivot для SharePoint 2013 конфигурации](../media/ssas-powerpivot-configtool-4-sharepoint2013-choosemode.gif "средство PowerPivot для SharePoint 2013 конфигурации")  
  
 Каждая задача состоит из индивидуальных действий, которые касаются определенных аспектов настройки сервера. Например, задача настройки включает действия по развертыванию решений, созданию приложения службы PowerPivot, активации компонентов и настройки обновления данных. Список действий зависит от текущего состояния установки. Если действие не требуется, средство исключает его из списка задач.  
  
 При нажатии кнопки «Пуск» средство обработает все действия в пакетном режиме. Несмотря на то что каждое действие отображается как отдельный элемент в списке задач, все действия в составе задачи обрабатываются вместе. Обрабатываются только те действия, которые проходят проверку. Для прохождения проверки, возможно, потребуется добавить или изменить некоторые из входных значений.  
  
## <a name="related-content"></a>См. также  
 [Обновление PowerPivot для SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) рассматривает рабочий процесс, который обновляет существующую установку, уже находящегося в ферме.  
  
 [Удаление PowerPivot для SharePoint](../../sql-server/install/uninstall-power-pivot-for-sharepoint.md) рассматривает рабочий процесс, который удаляет PowerPivot для служб, решения и страницы приложений из фермы SharePoint.  
  
 [Настройка PowerPivot с помощью Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [Настройка и администрирование сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
