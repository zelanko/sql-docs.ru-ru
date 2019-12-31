---
title: Мониторинг с помощью SCOM
description: Выполните следующие действия, чтобы настроить пакеты управления System Center Operations Manager (SCOM) для платформы аналитики. Пакеты управления необходимы для мониторинга системы платформы аналитики из SCOM.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 67029d235a1bc65b5ee0ab6f01f51dea42ebcc8b
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401302"
---
# <a name="configure-system-center-operations-manager-scom-to-monitor-analytics-platform-system"></a>Настройка System Center Operations Manager (SCOM) для мониторинга системы аналитики платформы
Выполните следующие действия, чтобы настроить пакеты управления System Center Operations Manager (SCOM) для платформы аналитики. Пакеты управления необходимы для мониторинга системы платформы аналитики из SCOM.  
  
## <a name="BeforeBegin"></a>Перед началом  
**Необходимые компоненты**  
  
Необходимо установить и запустить System Center Operations Manager 2007 R2.  
  
Пакеты управления должны быть установлены и настроены. См. статью [Установка пакетов управления scom &#40;Analytics Platform system&#41;](install-the-scom-management-packs.md) и [Импорт пакета управления scom для PDW &#40;analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
## <a name="ConfigureRunAsProfile"></a>Настройка профиля запуска от имени в System Center  
Чтобы настроить System Center, необходимо выполнить следующие действия.  
  
-   Создайте учетную запись запуска от имени для пользователя домена **наблюдателя APS** и сопоставьте ее с **учетной записью наблюдателя Microsoft APS.**  
  
-   Создайте учетную запись запуска от имени для пользователя **monitoring_user** ТД и сопоставьте ее с **учетной записью действия Microsoft APS**.  
  
Ниже приведены подробные инструкции по выполнению задач.  
  
1.  Создайте учетную запись запуска от имени **наблюдателя ТД** с типом учетной записи **Windows** для пользователя домена **наблюдателя APS** .  
  
    1.  Перейдите в область " **Администрирование** ", щелкните правой кнопкой мыши**учетные записи** **конфигурации** -> запуска от имени и выберите **создать учетную запись запуска от имени...**  
  
        ![конфигурескомкреатерунасаккаунт](./media/configure-scom-to-monitor-analytics-platform-system/ConfigureScomCreateRunAsAccount.png "конфигурескомкреатерунасаккаунт")  
  
    2.  Откроется диалоговое окно **мастера создания учетной записи запуска от имени** . На странице **Введение** нажмите кнопку **Далее**.  
  
    3.  На странице **Общие свойства** выберите **Windows** из **типа учетной записи запуска от имени** и укажите в качестве **отображаемого имени**"наблюдатель APS".  
  
        ![креатерунасаккаунтвизардженералпропертиес](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties.png "креатерунасаккаунтвизардженералпропертиес")  
  
    4.  На странице **учетные данные** ![креатерунасаккаунтвизардкредентиалс](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials.png "креатерунасаккаунтвизардкредентиалс")  
  
    5.  На странице **безопасность распространения** выберите **менее безопасное** и нажмите кнопку **создать** , чтобы завершить работу.  
  
        ![креатерунасаккаунтвизарддистрибутионсекурити](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardDistributionSecurity.png "креатерунасаккаунтвизарддистрибутионсекурити")  
  
        1.  Если вы решили использовать **более безопасный** вариант, необходимо вручную указать компьютеры, на которых будут распространяться учетные данные. Для этого после создания учетной записи запуска от имени щелкните ее правой кнопкой мыши и выберите пункт **Свойства**.  
  
        2.  Перейдите на вкладку **распространение** и **добавьте** нужные компьютеры.  
  
            ![рунасаккаунтпропертиес](./media/configure-scom-to-monitor-analytics-platform-system/RunAsAccountProperties.png "рунасаккаунтпропертиес")  
  
2.  Задайте профиль **учетной записи наблюдателя Microsoft APS** , чтобы использовать учетную запись запуска от имени **наблюдателя APS** .  
  
    1.  Перейдите в раздел **Администрирование** -> **Запуск от имени** -> **Профили**конфигурации.  
  
        ![администратионрунасконфигуратионпрофилес](./media/configure-scom-to-monitor-analytics-platform-system/AdministrationRunAsConfigurationProfiles.png "администратионрунасконфигуратионпрофилес")  
  
    2.  Щелкните правой кнопкой мыши **учетную запись наблюдателя APS (Майкрософт** ) и выберите пункт **свойства**.  
  
        ![микрософтапсватчераккаунтпропертиес](./media/configure-scom-to-monitor-analytics-platform-system/MicrosoftApsWatcherAccountProperties.png "микрософтапсватчераккаунтпропертиес")  
  
    3.  Откроется диалоговое окно **мастер профилей запуска от имени** . Пропустите страницу **Введение** , нажав кнопку **Далее**.  
  
    4.  На странице **Общие свойства** нажмите кнопку **Далее**.  
  
    5.  На странице **учетные записи запуска от имени** нажмите кнопку **Добавить...** и выберите ранее созданную учетную запись запуска от имени **наблюдателя APS** .  
  
        ![рунаспрофилевизардадд](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd.png "рунаспрофилевизардадд")  
  
    6.  Нажмите кнопку **сохранить** , чтобы завершить Назначение профиля.  
  
3.  Дождитесь завершения обнаружения управляющих устройств APS.  
  
    1.  Перейдите на панель " **мониторинг** " и откройте представление состояния устройства **SQL Server устройство** -> **Microsoft Analytics Platform System** -> **устройства** .  
  
        ![склсерверапплианцемикрософтапсапплианцес](./media/configure-scom-to-monitor-analytics-platform-system/SqlServerApplianceMicrosoftApsAppliances.png "склсерверапплианцемикрософтапсапплианцес")  
  
    2.  Подождите, пока устройство появится в списке. Имя устройства должно быть равно значению, указанному в реестре. После завершения обнаружения вы увидите все устройства, которые перечислены, но не отслеживаются. Чтобы включить мониторинг, выполните следующие действия.  
  
    > [!NOTE]  
    > Следующие шаги можно выполнить параллельно, пока ожидается завершение первоначального обнаружения устройства.  
  
4.  Создайте еще одну новую учетную запись запуска от имени для запроса ТД для получения данных о работоспособности.  
  
    1.  Начните создавать новую учетную запись запуска от имени, как описано в шаге 1.  
  
    2.  На странице **Общие свойства** выберите тип учетной записи " **Обычная проверка подлинности** ".  
  
        ![CreateRunAsAccountWizardGeneralProperties2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardGeneralProperties2.png "CreateRunAsAccountWizardGeneralProperties2")  
  
    3.  На странице **учетные данные** укажите допустимые учетные данные для доступа к DMV состояния работоспособности APS.  
  
        ![CreateRunAsAccountWizardCredentials2](./media/configure-scom-to-monitor-analytics-platform-system/CreateRunAsAccountWizardCredentials2.png "CreateRunAsAccountWizardCredentials2")  
  
5.  Настройте профиль **учетной записи действия Microsoft APS** , чтобы использовать только что созданную учетную запись запуска от имени для экземпляра APS.  
  
    1.  Перейдите к свойствам **учетной записи Microsoft APS Action** , как описано в шаге 2.  
  
    2.  На странице **учетные записи запуска от имени** нажмите кнопку **Добавить...** и 
    3.  Выберите только что созданную учетную запись запуска от имени.  
  
        ![RunAsProfileWizardAdd2](./media/configure-scom-to-monitor-analytics-platform-system/RunAsProfileWizardAdd2.png "RunAsProfileWizardAdd2")  
  
## <a name="next-step"></a>Дальнейшее действие  
Теперь, когда вы настроили пакеты управления, можно приступить к наблюдению за устройством. Дополнительные сведения см. [в статье мониторинг устройства с помощью System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
