---
title: Закрепление элементов служб Reporting Services на информационных панелях Power BI | Документы Майкрософт
ms.custom: ''
ms.date: 09/16/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pbi
- dashboard
- pin
- powerbi
- power bi integration
ms.assetid: 1d96c3f7-2fd4-40f7-8d1c-14a7f54cdb15
caps.latest.revision: 23
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 4065422e0be3f8570e91cc05d6c5cd2c86af24ec
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2018
ms.locfileid: "40405435"
---
# <a name="pin-reporting-services-items-to-power-bi-dashboards"></a>Закрепление элементов служб Reporting Services на информационных панелях Power BI
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] позволяют пользователям закрепить элементы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] из панели инструментов средства просмотра отчетов на информационной панели [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] в качестве новой плитки.   Для этого администратор должен сначала интегрировать сервер отчетов с Azure Active Directory и [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  
  
 ![rs_powerbi_icon](../reporting-services/media/ssrs-powerbi-icon.png "rs_powerbi_icon")  
  
 [!INCLUDE[applies](../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в основном режиме
  
##  <a name="bkmk_requirements_to_pin"></a> Требования для закрепления  
  
-   Сервер отчетов настроен для интеграции с [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] . Дополнительные сведения см. в разделе [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md). Если сервер отчетов не настроен, вы не увидите кнопку **Закрепить на информационной панели Power BI** на панели инструментов.  
  
     ![ssRS_Report_PowerBI](../reporting-services/media/ssrs-report-powerbi.png)  
  
-   Элемент закрепляется из средства просмотра отчетов [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], например `http://myserver/Reports`.  Невозможно закрепить элемент из [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)], из конструктора отчетов в [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]или с URL-адреса сервера отчетов.  Например: `http://myserver/ReportServer`.  
  
-   В браузере необходимо разрешить всплывающие окна на сайте сервера отчетов.  
  
-   Отчеты следует настроить для использования хранимых учетных данных, если вы хотите, чтобы закрепленный элемент обновлялся.  При закреплении элемента подписка [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] создается автоматически для управления обновлением данных элемента на информационной панели.  Если в отчете не используются сохраненные учетные данные, при запуске подписки появится сообщение, похожее на следующее сообщение на странице **Мои подписки** .  
  
        PowerBI Delivery error: dashboard: IT Spend Analysis Sample, visual: Chart2, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credential.
 
    См. раздел "Настройка сохраненных учетных данных для источника данных, связанного с отчетами (собственный режим)" статьи [Сохраненные учетные данные в источнике данных Reporting Services](../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md).  
  
##  <a name="bkmk_supported_items"></a> Элементы, которые вы можете закрепить  
 Следующие элементы отчета можно закрепить на информационной панели [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .  Вложенные в область данных элементы закрепить невозможно. Например, невозможно закрепить элемент, который вложен в таблицу или список [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   Диаграммы  
  
-   Панели датчиков  
  
-   Карты  
  
-   Изображения  
  
-   Элементы должны быть в тексте отчета.  Невозможно закрепить элементы в колонтитулах страницы.  
  
-   Вы можете закрепить отдельные элементы, расположенные в прямоугольнике верхнего уровня, но невозможно закрепить их все как одну группу.  
  
##  <a name="bkmk_to_pin"></a> Закрепление элемента отчета  
  
1. Убедитесь, что вы вошли в [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. В [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]щелкните пункт меню **Мои параметры** и выполните вход. См. дополнительные сведения о [странице "Мои параметры", используемой для интеграции с Power BI на веб-портале](http://msdn.microsoft.com/85c2fac7-80bf-45b7-8654-764b5f5231f5).

    ![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
2. Перейдите к папке [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] , содержащей отчет, и просмотрите его.  
  
3. При просмотре отчета нажмите кнопку **Закрепить в Power BI** на панели инструментов.  Вам будет предложено войти, если вы еще не сделали этого.  Если кнопка [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] не видна, сервер отчетов не интегрирован с [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Дополнительные сведения см. в разделе [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
    ![ssRS_Report_PowerBI](../reporting-services/media/ssrs-report-powerbi.png)  
  
4. Выберите элемент отчета, чтобы закрепить его в [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Одновременно можно закрепить только один элемент.  Средство просмотра отчетов отображает затененное представление отчета. Элементы отчета, которые вы можете закрепить, будут выделены, а элементы, которые невозможно закрепить, будут затенены.  
  
    **(1)** Выберите группу, содержащую панель мониторинга, на которой нужно закрепить элемент; **(2)** выберите панель мониторинга, на которой требуется закрепить элемент; и **(3)** выберите частоту обновления плитки на этой панели мониторинга.   ![примечание](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "примечание") Обновлением управляют подписки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], а после закрепления элемента можно изменить подписку и настроить другое расписание обновления.  
  
    ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png)  
  
5. Выберите **Закрепить**.  
  
    В диалоговом окне **Успешно закреплено** щелкните ссылку **См. это в Power BI** , чтобы перейти к панели мониторинга и просмотреть закрепленный элемент.  
  
6. Нажмите кнопку **Закрыть** для возврата в обычное представление.  
  
##  <a name="bkmk_in_the_dashboard"></a> На панели мониторинга

После закрепления элемента отчета на информационной панели плитка выглядит как другие плитки информационной панели и не существует видимых изменений плитки от [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. В следующем списке представлена сводная информация о заполнении свойств плиток из элемента отчета.  
  
Из информационной панели [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] закрепленный элемент отчета действует, как другие плитки:

**(1)** Вы можете закрепить плитку на другие панели мониторинга.

**(2)** В разделе **Сведения о плитке** можно увидеть, что заголовок отчета [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] используется в качестве заголовка по умолчанию плитки.

**(3)** Подзаголовок плитки основан на дате и времени закрепления плитки или дате последнего обновления из [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Расписание обновления управляется подпиской [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , которая была автоматически создана при закреплении элемента отчета.

**(4)** Если щелкнуть саму плитку, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] использует **(3) настраиваемую ссылку** для перехода на страницу [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] зарегистрированного сервера отчетов. Ссылка была создана при закреплении элемента из [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Если сервер отчетов не подключен к Интернету, вы увидите ошибку в браузере.  

![ssrs_pinned_tile_details](../reporting-services/media/ssrs-pinned-tile-details.png "ssrs_pinned_tile_details")  
  
##  <a name="bkmk-troubleshoot"></a> Устранение неполадок  
  
-   **Нет кнопки [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] на панели инструментов средства просмотра отчетов:** это означает, что сервер отчетов не был интегрирован с [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Дополнительные сведения см. в разделе [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
- **Не удается закрепить элемент**: при попытке закрепления элемента отображается следующее сообщение об ошибке. См. раздел [Элементы, которые вы можете закрепить](#bkmk_supported_items).  
  
      Cannot Pin: There are no report items on this page that you can pin to [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  
  
-   **Закрепленные элементы отображают устаревшие данные** на панели мониторинга [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] , и какое-то время они обновлялись.  Истек срок действия маркера учетных данных пользователя, и вам необходимо снова выполнить вход.  Регистрация учетных данных пользователя в Azure и [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] действует 90 дней. В[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]щелкните **Мои параметры**. Дополнительные сведения см. в статье [Страница "Мои параметры", используемая для интеграции с Power BI (диспетчер отчетов)](http://msdn.microsoft.com/85c2fac7-80bf-45b7-8654-764b5f5231f5).  
  
-   **Закрепленные элементы отображают устаревшие данные** на информационной панели [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] , и они ни разу не обновлялись.  Проблема состоит в том, что отчет не настроен на использование сохраненных учетных данных. Отчет должен использовать сохраненные учетные данные, так как во время закрепления элемента отчета создается подписка [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для управления расписанием обновления плиток. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] требуются сохраненные учетные данные. При просмотре страницы **Мои подписки** отображается сообщение об ошибке следующего вида:  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image3, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credentials are not stored in the report server database, or the user data source is configured not to require credentials but the unattended execution account is not specified. (rsInvalidDataSourceCredentialSetting)
  
-   **Истек срок действия учетных данных Power BI:**  при попытке закрепления элемента появляется следующее сообщение об ошибке. В [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]щелкните **Мои параметры** и на странице "Мои параметры" щелкните **Войти**. См. дополнительные сведения о [странице "Мои параметры", используемой для интеграции с Power BI на веб-портале](http://msdn.microsoft.com/85c2fac7-80bf-45b7-8654-764b5f5231f5).  
  
        Cannot Pin : Unexpected Server Error: Missing, invalid or expired Power BI credentials.  
  
-   **Невозможно закрепить**. Если вы попытаетесь закрепить элемент на панели мониторинга, которая доступна только для чтения, появится следующее сообщение об ошибке:  
  
        Server Error : The item 'Dashboard deleted 015cf022-8e2f-462e-88e5-75ab0a04c4d0' cannot be found. (rsItemNotFound)  
  
##  <a name="bkmk_subscription_management"></a> Управление подпиской  
 В дополнение к проблемам, связанным с подписками, описанными в разделе об устранении неполадок, следующие сведения помогут вам поддерживать подписки, связанные с [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .
  
-   **Имя элемента изменено.** Если закрепленный элемент отчета переименован или удален, плитка [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] не будет обновляться и вы увидите следующее сообщение об ошибке.  Если изменить имя элемента на исходное, подписка снова начнет работать, а плитка будет обновляться по расписанию подписок.  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image1, error: Error: Report item 'Image1' cannot be found.  
  
     Кроме того, можно изменить свойства подписки и изменить **визуальное имя отчета** на соответствующее имя элемента отчета. ![изменение визуального элемента, используемого для обновления power bi](../reporting-services/media/ssrs-powerbi-subscription-visual.png "изменение визуального элемента, используемого для обновления power bi")  
  
-   **Удаление плитки**. При удалении плитки в [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]связанная подписка не будет удалена в [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и на странице **Мои подписки**и появится сообщение об ошибке следующего вида. Вы можете удалить подписку.  
  
        PowerBI Delivery error: dashboard: SSRS items, visual: Image3, error: The item 'Tile deleted af7131d9-5eaf-480f-ba45-943a07d19c9f' cannot be found.  

## <a name="video"></a>Видеоролик

<iframe width="560" height="315" src="https://www.youtube.com/embed/QhPQObqmMPc" frameborder="0" allowfullscreen></iframe>

## <a name="see-also"></a>См. также:  
 [Интеграция сервера отчетов с Power BI (диспетчер конфигурации)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
 [Страница "Мои параметры", используемая для интеграции с Power BI на веб-портале](http://msdn.microsoft.com/85c2fac7-80bf-45b7-8654-764b5f5231f5)  
 [Панели мониторинга в Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

