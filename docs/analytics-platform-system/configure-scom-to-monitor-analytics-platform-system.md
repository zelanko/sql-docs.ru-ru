---
title: Настройка SCOM для наблюдения за Analytics Platform System | Документы Microsoft
description: Выполните следующие действия для настройки пакетов управления System Center Operations Manager (SCOM) для Analytics Platform System. Необходимые пакеты управления для отслеживания система платформы аналитики из SCOM.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4c2e8a42d488c18e705c9d7d8c1d53c9ff7c9cb8
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>Настройка System Center Operations Manager (SCOM) для наблюдения за система платформы аналитики
Выполните следующие действия для настройки пакетов управления System Center Operations Manager (SCOM) для Analytics Platform System. Необходимые пакеты управления для отслеживания система платформы аналитики из SCOM.  
  
## <a name="BeforeBegin"></a>Перед началом  
**Предварительные требования**  
  
System Center Operations Manager 2007 R2 должны быть установлены и запущены.  
  
Пакеты управления должен быть установлен и настроен. В разделе [установить пакеты управления SCOM &#40;Analytics Platform System&#41; ](install-the-scom-management-packs.md) и [импорта пакета управления SCOM для PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="ConfigureRunAsProfile"></a>Настройте профиль запуска от имени в System Center  
Чтобы настроить System Center, необходимо выполнить следующие шаги:  
  
-   Создать запись запуска от имени для **APS наблюдателя** пользователя домена и сопоставить его с **учетной записи Майкрософт APS наблюдателя.**  
  
-   Создать запись запуска от имени для **monitoring_user** APS пользователя и сопоставить его с **учетная запись действия APS Microsoft**.  
  
Ниже приведены подробные инструкции для выполнения задач.  
  
1.  Создание **APS наблюдателя** учетная запись запуска от **Windows** тип счета **APS наблюдателя** пользователя домена.  
  
    1.  Перейдите к **администрирования** щелкните правой кнопкой мыши на **Настройка запуска от имени** -> **учетные записи** и выберите **Создание учетной записи запуска...**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  **Запуска мастера создания от имени учетной записи** откроется диалоговое окно. На **Введение** щелкните **Далее**.  
  
    3.  На **общие свойства** выберите **Windows** из **тип учетной записи запуска от** и укажите в качестве «Наблюдатель APS» **отображаемое имя**.  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  На **учетные данные** страницы, ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  На **безопасности распространителя** выберите **опаснее** и нажмите кнопку **создать** кнопки завершения.  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  Если вы решили использовать **более безопасные** параметр, необходимо вручную указать компьютеры, на которых будет распространяться учетные данные. Чтобы сделать это, после создания учетной записи запуска от имени, щелкните его правой кнопкой мыши и выберите **свойства**.  
  
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
  
    2.  Подождите, пока устройство появится в списке. Имя устройства должно быть равно указанному в реестре. После завершения обнаружения вы увидите, что все устройства в списке, но не отслеживается. Чтобы включить мониторинг, выполните следующие шаги.  
  
    > [!NOTE]  
    > Следующие шаги можно выполнить параллельно, пока ожидается для обнаружения начального устройство для завершения.  
  
4.  Создайте другой новый запуск от имени учетной записи для запроса APS для получения данных работоспособности.  
  
    1.  Начать создание новой учетной записи запуска от имени, как описано в шаге 1.  
  
    2.  На **общие свойства** выберите **обычной проверки подлинности** тип учетной записи.  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  На **учетные данные** введите действительные учетные данные для доступа к состоянию работоспособности APS динамических административных представлений.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Настройка **учетная запись действия APS Microsoft** профиль для использования только что созданная учетная запись запуска от имени для экземпляра APS.  
  
    1.  Перейдите к **учетная запись действия APS Microsoft** свойства, как описано в шаге 2.  
  
    2.  На **учетные записи запуска от** щелкните **добавить...** и 
    3.  Выберите только что созданная учетная запись запуска от имени.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Следующий шаг  
Настройки пакетов управления, вы готовы начать мониторинг устройства. Дополнительные сведения см. в разделе [отслеживать устройства с помощью System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
