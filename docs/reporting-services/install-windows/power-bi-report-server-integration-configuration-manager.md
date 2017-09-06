---
title: "Питание интеграция сервера отчетов BI (диспетчер конфигурации) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pbi
- power bi
- power bi integration
ms.assetid: 902b7c31-7399-4855-90f2-42f89d847fff
caps.latest.revision: 22
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: 3d39c8851c43adba12102f7d2440ae55e8216e1e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/17/2017

---

# <a name="power-bi-report-server-integration-configuration-manager"></a>Интеграция сервера отчетов с Power BI (диспетчер конфигурации)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Страница  **Интеграция с Power BI** в диспетчере конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] используется для регистрации сервера отчетов в нужном управляемом клиенте Azure Active Directory (AD), чтобы предоставить пользователям сервера отчетов возможность закрепления поддерживаемых элементов отчетов на панелях мониторинга [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] . Список поддерживаемых элементов, которые можно закреплять, см. в статье [Закрепление элементов служб Reporting Services на информационных панелях Power BI](../../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md).

![rs_powerbi_icon](../../reporting-services/media/ssrs-powerbi-icon.png "rs_powerbi_icon")

##  <a name="bkmk_requirements"></a> Требования к интеграции с Power BI

Помимо подключения к Интернету, необходимого для перехода к службе [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] , для обеспечения интеграции [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)]нужно выполнить приведенные ниже требования.

- **Azure Active Directory.** Организация должна использовать Azure Active Directory для управления каталогами и удостоверениями служб Azure и веб-приложений. Дополнительные сведения см. в разделе [Что такое Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-whatis/).

- **Управляемый клиент.** Панель мониторинга [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] , на которой будут закрепляться элементы отчетов, должна входить в управляемый клиент Azure AD.  Управляемый клиент создается автоматически во время оформления первой подписки на службы Azure, такие как Office 365 и Microsoft Intune.   Распространенные клиенты сейчас не поддерживается.  Дополнительные сведения см. в подразделах "Что такое клиент Azure AD" и "Какую версию Azure AD выбрать" в разделе [Что такое Azure Active Directory?](https://msdn.microsoft.com/library/azure/jj573650.aspx#BKMK_WhatIsAnAzureADTenant).

- Пользователь, выполняющий интеграцию [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] , должен быть членом клиента Azure AD, системным администратором [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и системным администратором базы данных каталога ReportServer.

- Пользователь, выполняющий интеграцию [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] , должен запустить диспетчер конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с использованием учетной записи, применяемой для установки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], или учетной записи, с помощью которой запущена служба [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

- Отчеты, элементы которых нужно закрепить, должны использовать сохраненные учетные данные. Это требование не самой интеграции [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] , а процесса обновления для закрепленных элементов.  Во время закрепления элемента отчета создается подписка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для управления расписанием обновления плиток в [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требуются сохраненные учетные данные. Если отчет не использует сохраненные учетные данные, пользователь может по-прежнему закреплять элементы отчетов, но, когда связанная подписка попытается обновить данные в [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)], появится сообщение об ошибке, аналогичное отображаемому на странице **Мои подписки** .

        PowerBI Delivery error: dashboard: IT Spend Analysis Sample, visual: Chart2, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credential.

Дополнительные сведения о том, как хранить учетные данные, см. в разделе «Настройка сохраненных учетных данных для источника данных отчета» в [хранить учетные данные в источнике данных Reporting Services](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md).

Администратор может просмотреть файлы журнала  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для получения дополнительной информации.  Будут отображены сообщения, аналогичные приведенным далее. ![Примечание](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "Примечание") это отличный способ проверки и отслеживания [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] файлы журналов заключается в использовании [!INCLUDE[msCoName](../../includes/msconame-md.md)] Power Query над файлами.  Дополнительные сведения и короткий видео ролик см. в документе [Report Server Service Trace Log](../../reporting-services/report-server/report-server-service-trace-log.md).

    subscription!WindowsService_1!1458!09/24/2015-00:09:27:: e ERROR: PowerBI Delivery error: dashboard: IT Spend Analysis Sample, visual: Chart2, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credentials are not stored in the report server database, or the user data source is configured not to require credentials but the unattended execution account is not specified.

    notification!WindowsService_1!1458!09/24/2015-00:09:27:: e ERROR: Error occurred processing subscription fcdb8581-d763-4b3b-ba3e-8572360df4f9: PowerBI Delivery error: dashboard: IT Spend Analysis Sample, visual: Chart2, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared data set. Either the user data source credentials are not stored in the report server database, or the user data source is configured not to require credentials but the unattended execution account is not specified.

##  <a name="bkmk_steps2integrate"></a> Интеграция и регистрация сервера отчетов

В диспетчере конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выполните приведенные ниже действия. Дополнительные сведения см. в разделе [диспетчер конфигурации служб Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).

1. Откройте страницу интеграции [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] .

     ![rs_powerbi_integration](../../reporting-services/install-windows/media/ssrs-powerbi-integration.png "rs_powerbi_integration")

2. Выберите **Зарегистрировать в Power BI**.

3. В диалоговом окне входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] введите учетные данные, используемые для входа в [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)].

4. После завершения регистрации в разделе **Сведения о регистрации в Power BI** появятся идентификатор клиента Azure и URL-адреса перенаправления.  URL-адреса используются в ходе процесса входа для панели мониторинга [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] с целью взаимодействия с зарегистрированным сервером отчетов.

5. ![Примечание](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "Примечание") выберите **копирования** кнопку в **результатов** чтобы скопировать сведения о регистрации в буфер обмена Windows, и их можно сохранить для дальнейшего использования.

##  <a name="bkmk_unregister"></a> Отмена регистрации в Power BI

**Отменить регистрацию.** Отмена регистрации сервера отчетов в Azure Active Directory приведет к следующим результатам:

- **Мои параметры** ссылка больше не будет отображаться в строке меню портала web.

- Элементы отчетов, которые уже были закреплены, останутся на панелях мониторинга, но плитки обновляться не будут.

- Подписки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые обновляли плитки, по-прежнему будут существовать на сервере отчетов, но при запуске по настроенному расписанию для них будет выводиться сообщение об ошибке следующего вида.

    **Не удалось загрузить модуль доставки для данной подписки.**

На странице **Power BI** диспетчера конфигурации нажмите кнопку **Отменить регистрацию в Power BI** .

##  <a name="bkmk_updateregistration"></a> Обновление регистрации

В случае изменения конфигурации сервера отчетов воспользуйтесь функцией **обновления регистрации** . Обновление требуется, если, например, нужно добавить или удалить URL-адреса, используемые для перехода к [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)].

- В диспетчере конфигураций [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выберите **URL-адрес веб-портала**.

     Выберите **Дополнительно**.

- Выберите **Добавить** , чтобы добавить новое удостоверение для [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] , и нажмите кнопку **ОК**.

     Значок [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] изменится и будет указывать на изменение конфигурации сервера.  ![ssrs_powebi_icon_warning](../../reporting-services/install-windows/media/ssrs-powebi-icon-warning.png "ssrs_powebi_icon_warning")

- На странице **Интеграция с Power BI** нажмите кнопку **Обновить регистрацию**.

     Вам будет предложено войти в Azure AD. На обновленной странице в списке **URL-адреса перенаправления**появится новый URL-адрес.

##  <a name="bkmk_integration_process"></a> Сводные данные по процессу интеграции с Power BI и закреплению элементов

В этих разделах содержатся сводные данные по основным действиям и технологиям, используемым для интеграции сервера отчетов с [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] и закрепления элементов отчетов на панели мониторинга.

 **Интеграция**

1. После нажатия кнопки **Регистрация в Power BI** в диспетчере конфигурации вам будет предложено выполнить вход в Azure Active Directory.

2. Клиентское приложение [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] регистрируется в управляемом клиенте.

3. Управляемый клиент в Azure Active Directory используется для создания клиентского приложения Power BI.

4. Регистрация связана с URL-адресами перенаправления, используемыми при входе пользователей с сервера отчетов.  Идентификатор приложения и URL-адреса сохраняются в базе данных ReportServer. URL-адрес перенаправления используется во время вызовов проверки подлинности в Azure, поэтому вызов может быть возвращен на сервер отчетов. Например, когда пользователь входит в или закреплять элементы на панель мониторинга.

5. Идентификатор приложения и URL-адреса отображаются в Configuration Manager.

 ![ssrs_pbiflow_integration](../../reporting-services/install-windows/media/ssrs-pbiflow-integration.png "ssrs_pbiflow_integration")

 **Пользователь закрепляет элемент отчета на панели мониторинга**

1. Пользователь просматривает отчеты в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] и при первом закреплении элемента отчета из [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]

2. он будет перенаправлен на страницу входа в Azure AD. Кроме того, выполнить вход можно со страницы [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] **My Settings** page. Когда пользователь входит в управляемый клиент Azure, между его учетной записью Azure и разрешениями [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливается связь.  Дополнительные сведения см. в разделе [Страница "Мои параметры", используемая для интеграции с Power BI (диспетчер отчетов)](http://msdn.microsoft.com/en-us/85c2fac7-80bf-45b7-8654-764b5f5231f5).

3. Маркер безопасности пользователя возвращается на сервер отчетов и

4. сохраняется в базе данных ReportServer.

5. Список панелей мониторинга, доступ к которым имеет пользователь, извлекается из службы [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] .  Пользователь выбирает целевую группу и панель мониторинга и настраивает частоту обновления данных на плитке [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] .

6. Элемент отчета закрепляется на панели мониторинга.

7. Создается подписка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для управления запланированным обновлением элемента отчета на плитке панели мониторинга. Подписка использует маркер безопасности, который был создан при входе пользователя в систему.

     **ПРИМЕЧАНИЕ.**  Маркер действует в течение **90 дней**, после чего пользователю необходимо выполнить вход еще раз, чтобы создать маркер. По истечении срока действия маркера закрепленные плитки по-прежнему будут отображаться на панели мониторинга, но данные обновляться не будут.  Для подписок, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] используемых для закрепленных элементов, будут выводиться сообщения об ошибках до тех пор, пока не будет создан новый маркер пользователя. См. статью [Страница "Мои параметры", используемая для интеграции с Power BI (диспетчер отчетов)](http://msdn.microsoft.com/en-us/85c2fac7-80bf-45b7-8654-764b5f5231f5). для получения дополнительных сведений.

Когда пользователь закрепляет элемент второй раз, шаги 1–4 пропускаются. Вместо них из базы данных ReportServer извлекается идентификатор приложения и URL-адреса, и поток продолжается с шага 5.

![ssRS-pin-to-powerbi-flow](../../reporting-services/install-windows/media/ssrs-pin-to-powerbi-flow.png)

 **Срабатывание подписки для обновления плитки панели мониторинга**

1. При срабатывании подписки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] происходит отображение отчета

2. и извлечение маркера пользователя из базы данных ReportServer.

3. Состояние и данные элемента отчета отправляются с маркером в службу [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)].

4. Маркер отправляется в Azure AD для проверки. Если маркер является допустимым, данные элемента отчета отправляются в плитку панели мониторинга, после чего обновляется свойство даты плитки.

5. Если маркер является недопустимым, возвращается ошибка, которая регистрируется на сервере отчетов.  На панель мониторинга не отправляются сведения о состоянии или другая информация.

![ssRS-subscription-to-powerbi-flow](../../reporting-services/install-windows/media/ssrs-subscription-to-powerbi-flow.png)

<iframe width="560" height="315" src="https://www.youtube.com/embed/QhPQObqmMPc" frameborder="0" allowfullscreen></iframe>

## <a name="next-steps"></a>Следующие шаги

[Мои параметры для интеграции с Power BI](http://msdn.microsoft.com/en-us/85c2fac7-80bf-45b7-8654-764b5f5231f5)  
[Закрепление элементов служб Reporting Services на информационных панелях Power BI](../../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
[Панели мониторинга в Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
