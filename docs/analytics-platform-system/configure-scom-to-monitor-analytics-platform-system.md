---
title: "Настройка SCOM для наблюдения за система платформы аналитики"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4dba9b50-1447-45fc-b219-b9fc99d47d8d
caps.latest.revision: "10"
ms.openlocfilehash: 435bbae75548d1959d509b9833bd9a6f7ec658e2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="configure-scom-to-monitor-analytics-platform-system"></a>Настройка SCOM для наблюдения за система платформы аналитики
Выполните следующие действия для настройки пакетов управления System Center Operations Manager (SCOM) для Analytics Platform System. Необходимые пакеты управления для отслеживания система платформы аналитики из SCOM.  
  
## <a name="BeforeBegin"></a>Перед началом  
**Предварительные требования**  
  
System Center Operations Manager 2007 R2 должны быть установлены и запущены.  
  
Пакеты управления должен быть установлен и настроен. В разделе [установить пакеты управления SCOM &#40; Система платформы аналитики &#41; ](install-the-scom-management-packs.md) и [импортировать пакет управления SCOM для PDW &#40; Система платформы аналитики &#41; ](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="ConfigureRunAsProfile"></a>Настройте профиль запуска от имени в System Center  
Для настройки System Center необходимо выполнить следующие шаги:  
  
-   Создать запись запуска от имени для **APS наблюдателя** пользователя домена и сопоставить его с **учетной записи Майкрософт APS наблюдателя.**  
  
-   Создать запись запуска от имени для **monitoring_user** APS пользователя и сопоставить его с **учетная запись действия APS Microsoft**.  
  
Ниже приведены подробные инструкции о том, как это сделать.  
  
1.  Создание **APS наблюдателя** учетная запись запуска от **Windows** тип счета **APS наблюдателя** пользователя домена.  
  
    1.  Перейдите к **администрирования** щелкните правой кнопкой мыши на **Настройка запуска от имени** -> **учетные записи** и выберите **Создание учетной записи запуска...**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  **Запуска мастера создания от имени учетной записи** откроется диалоговое окно. На **Введение** щелкните **Далее**.  
  
    3.  На **общие свойства** выберите **Windows** из **тип учетной записи запуска от** и укажите в качестве «Наблюдатель APS» **отображаемое имя**.  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  На **учетные данные** введите учетные данные пользователя домена «APS наблюдатель».  
  
        ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  На **безопасности распространителя** выберите **опаснее** и нажмите кнопку **создать** кнопки завершения.  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  Если вы решили использовать **более безопасные** параметр, необходимо вручную указать компьютеры какие учетные данные будут распространяться. Чтобы сделать это, после создания учетной записи запуска от имени, щелкните его правой кнопкой мыши и выберите **свойства**.  
  
        2.  Перейдите к **распространения** вкладку и **добавить** требуемого компьютеров.  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  Задать **учетной записи Майкрософт APS наблюдателя** профиль для использования **APS наблюдателя** учетная запись запуска от имени.  
  
    1.  Перейдите к **администрирования** -> **Настройка запуска от имени** -> **профилей**.  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  Щелкните правой кнопкой мыши **учетной записи Майкрософт APS наблюдателя** из списка и выберите **свойства**.  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  **Мастера запуска от имени профиля** откроется диалоговое окно. Пропустить **Введение** , нажав кнопку **Далее**.  
  
    4.  На **общие свойства** щелкните **Далее**.  
  
    5.  На **учетные записи запуска от** щелкните **добавить...** и выберите ранее созданный **APS наблюдателя** учетная запись запуска от имени.  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  Нажмите кнопку **Сохранить** завершения назначения профиля.  
  
3.  Дождитесь завершения обнаружения устройств APS.  
  
    1.  Перейдите к **мониторинг** область и откройте **устройстве SQL Server** -> **Microsoft Analytics Platform System**  ->   **Устройства** представление состояния.  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  Подождите, пока устройство появится в списке. Имя устройства должно быть равно указанному в реестре.  
  
    После завершения обнаружения вы увидите, что все устройства в списке, но не отслеживается. Для отслеживания работы, выполните следующие шаги.  
  
    > [!NOTE]  
    > Следующие шаги можно выполнить параллельно, пока ожидается для обнаружения начального устройство для завершения.  
  
4.  Создайте другой новый запуск от имени учетной записи для запроса APS для получения данных работоспособности.  
  
    1.  Начать создание новой учетной записи запуска от имени, как описано в шаге 1.  
  
    2.  На **общие свойства** выберите **обычной проверки подлинности** тип учетной записи.  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  На **учетные данные** страницы питания действительные учетные данные для доступа к состоянию работоспособности APS динамических административных представлений.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Настройка **учетная запись действия APS Microsoft** профиль для использования только что созданная учетная запись запуска от имени для экземпляра APS.  
  
    1.  Перейдите к **учетная запись действия APS Microsoft** свойства, как описано в шаге 2.  
  
    2.  На **учетные записи запуска от** щелкните **добавить...** и выберите только что созданная учетная запись запуска от имени.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Следующий шаг  
Настройки пакетов управления, вы готовы начать мониторинг устройства. Дополнительные сведения см. в разделе [отслеживать устройства с помощью System Center Operations Manager &#40; Система платформы аналитики &#41; ](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
