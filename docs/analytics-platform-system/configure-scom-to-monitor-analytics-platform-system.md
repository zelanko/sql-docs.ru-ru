---
title: Настройка SCOM для мониторинга Analytics Platform System | Документация Майкрософт
description: Выполните следующие действия для настройки пакетов управления System Center Operations Manager (SCOM) для Analytics Platform System. Пакеты управления, необходимые для мониторинга Analytics Platform System из SCOM.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5ec495b3dd321f712aed54fb3b337efe85719be5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961239"
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>Настройка System Center Operations Manager (SCOM) для мониторинга Analytics Platform System
Выполните следующие действия для настройки пакетов управления System Center Operations Manager (SCOM) для Analytics Platform System. Пакеты управления, необходимые для мониторинга Analytics Platform System из SCOM.  
  
## <a name="BeforeBegin"></a>Перед началом  
**Предварительные требования**  
  
System Center Operations Manager 2007 R2 должны быть установлены и запущены.  
  
Пакеты управления должен быть установлен и настроен. См. в разделе [установить пакеты управления SCOM &#40;Analytics Platform System&#41; ](install-the-scom-management-packs.md) и [Импорт пакета управления SCOM для PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="ConfigureRunAsProfile"></a>Настройте профиль запуска от имени в System Center  
Чтобы настроить System Center, необходимо выполните следующие действия:  
  
-   Учетная запись запуска от имени для **APS наблюдателя** пользователя домена и сопоставить его с **учетной записи Майкрософт APS наблюдателя.**  
  
-   Учетная запись запуска от имени для **monitoring_user** APS пользователя и сопоставить его с **учетная запись действия APS Microsoft**.  
  
Ниже приведены подробные инструкции о том, как выполнить задачи.  
  
1.  Создание **APS наблюдателя** учетная запись запуска от **Windows** тип счета **APS наблюдателя** пользователя домена.  
  
    1.  Перейдите к **администрирования** панели, щелкните правой кнопкой мыши **Настройка запуска от имени** -> **учетные записи** и выберите **создать запись запуска от имени...**  
  
        ![ConfigureScomCreateRunAsAccount](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "ConfigureScomCreateRunAsAccount")  
  
    2.  **Создание мастера запуска от имени учетной записи** откроется диалоговое окно. На **Введение** щелкните **Далее**.  
  
    3.  На **общие свойства** выберите **Windows** из **тип учетной записи запуска от** и укажите в качестве «APS наблюдателя» **отображаемое имя**.  
  
        ![CreateRunAsAccountWizardGeneralProperties](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "CreateRunAsAccountWizardGeneralProperties")  
  
    4.  На **учетные данные** странице ![CreateRunAsAccountWizardCredentials](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "CreateRunAsAccountWizardCredentials")  
  
    5.  На **безопасность распространения** выберите **опаснее** и нажмите кнопку **создать** кнопку для завершения.  
  
        ![CreateRunAsAccountWizardDistributionSecurity](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "CreateRunAsAccountWizardDistributionSecurity")  
  
        1.  Если вы решили использовать **безопаснее** параметр, необходимо вручную указать компьютеры, на которые будет распространяться учетные данные. Чтобы сделать это, после создания учетной записи запуска от имени, его правой кнопкой мыши и выберите **свойства**.  
  
        2.  Перейдите к **распространения** вкладку и **добавить** требуемого компьютеров.  
  
            ![RunAsAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "RunAsAccountProperties")  
  
2.  Задайте **учетной записи Майкрософт APS наблюдателя** профиль, используемый **APS наблюдателя** учетной записи запуска от имени.  
  
    1.  Перейдите к **администрирования** -> **Настройка запуска от имени** -> **профили**.  
  
        ![AdministrationRunAsConfigurationProfiles](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "AdministrationRunAsConfigurationProfiles")  
  
    2.  Щелкните правой кнопкой мыши **учетной записи Майкрософт APS наблюдателя** из списка, а затем **свойства**.  
  
        ![MicrosoftApsWatcherAccountProperties](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "MicrosoftApsWatcherAccountProperties")  
  
    3.  **Мастера запуска от имени профиля** откроется диалоговое окно. Пропустить **Введение** страницу, нажав кнопку **Далее**.  
  
    4.  На **общие свойства** щелкните **Далее**.  
  
    5.  На **Run As Accounts** щелкните **добавить...**  и выберите ранее созданный **APS наблюдателя** учетной записи запуска от имени.  
  
        ![RunAsProfileWizardAdd](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "RunAsProfileWizardAdd")  
  
    6.  Нажмите кнопку **Сохранить** чтобы завершить Назначение профиля.  
  
3.  Дождитесь завершения обнаружения устройства APS.  
  
    1.  Перейдите к **мониторинг** области и откройте **SQL Server Appliance** -> **Microsoft Analytics Platform System**  ->   **Устройства** представление состояния.  
  
        ![SqlServerApplianceMicrosoftApsAppliances](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "SqlServerApplianceMicrosoftApsAppliances")  
  
    2.  Подождите, пока устройство появится в списке. Имя устройства должно быть равно единице в реестре. После завершения обнаружения вы увидите все устройства в списке, но не отслеживается. Чтобы включить мониторинг, выполните следующие шаги.  
  
    > [!NOTE]  
    > Дальнейшие действия можно выполнить параллельно, пока ожидают выполнения начальной устройство обнаружения.  
  
4.  Создайте другую новую учетную запись запуска для запроса APS для извлечения данных о работоспособности.  
  
    1.  Приступить к созданию новой учетной записи запуска от имени, как описано в шаге 1.  
  
    2.  На **общие свойства** выберите **обычной проверки подлинности** тип учетной записи.  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  На **учетные данные** странице, предоставить действительные учетные данные для доступа к состоянию работоспособности APS динамических административных представлений.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Настройка **учетная запись действия APS Microsoft** профиль для использования созданной учетной записи запуска от имени для экземпляра APS.  
  
    1.  Перейдите к **учетная запись действия APS Microsoft** свойства, как описано в шаге 2.  
  
    2.  На **Run As Accounts** щелкните **добавить...**  и 
    3.  Выберите только что созданная учетная запись запуска от имени.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Следующий шаг  
Теперь, когда вы настроили пакеты управления, вы готовы начать наблюдение за устройства. Дополнительные сведения см. в разделе [мониторинг устройства с помощью System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
