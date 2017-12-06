---
title: "Настройка электронной почты для приложения служб Reporting Services | Документы Майкрософт"
ms.custom: 
ms.date: 05/10/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: pro-bi
ms.technology: reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
caps.latest.revision: "13"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c5793b034bb69eeb35328de952736a5420889fa7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="configure-e-mail-for-a-reporting-services-service-application"></a>Настройка электронной почты для приложения служб Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Функция предупреждения об изменении данных служб отправляет предупреждения в сообщениях электронной почты. Для отправки электронной почты могут потребоваться настройка приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и изменение модуля доставки электронной почты приложением службы. Необходимо настроить параметры электронной почты и в том случае, если планируется использование модуля доставки электронной почты функцией подписки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.
  
### <a name="to-configure-e-mail-for-the-shared-service"></a>Настройка электронной почты для общей службы  
  
1.  В центре администрирования SharePoint перейдите на страницу **Управление приложением**.  
  
2.  В группе **Приложения службы** выберите пункт **Управление приложениями службы**.  
  
3.  В списке **Имя** выберите имя нужного приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
4.  Нажмите кнопку **Параметры электронной почты** на странице **Управление приложением служб Reporting Services** .  
  
5.  Установите флажок **Использовать SMTP-сервер**.  
  
6.  В поле **Исходящий SMTP-сервер** введите имя SMTP-сервера.  
  
7.  В поле **Адрес отправителя** введите адрес электронной почты.  
  
     Этот адрес будет использоваться как адрес отправителя всех электронных сообщений с предупреждениями.  
  
     Учетная запись пользователя, указанная в поле **Адрес отправителя** , должна быть управляемой учетной записью, указанной при настройке пула приложений для приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Если имеются необходимые разрешения, можно просмотреть список существующих управляемых учетных записей на странице «Учетные записи службы» центра администрирования SharePoint.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a>Проверка подлинности NTLM  
  
1.  Если среда электронной почты требует проверки подлинности NTLM и не поддерживает анонимный доступ, необходимо изменить настройки модуля доставки электронной почты приложениям службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Например, если вы видите следующее сообщение в поле **Последние результаты** для подписок на странице **Управление подписками** :  
  
    -   Сбой при отправке электронной почты: SMTP-серверу требуется безопасное соединение или клиент не прошел проверку подлинности. Получен ответ сервера. 5.7.1 Клиент не прошел проверку подлинности. Повторная отправка почты произведена не будет.  
  
     Укажите для параметра **SMTPAuthenticate** значение «2». Это значение нельзя изменить через пользовательский интерфейс. Следующий пример скрипта PowerShell обновляет полную конфигурацию расширения сервера отчетов для доставки электронной почты приложением службы с именем «SSRS_TESTAPPLICATION». Обратите внимание, что некоторые перечисленные в скрипте узлы (например, адрес отправителя) можно также задать через пользовательский интерфейс.  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
    $emailXml = [xml]$emailCfg   
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = “your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = “your FROM email address”  
    Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  Если нужно проверить имя приложения службы, запустите **командлет Get-SPRSServiceApplication**.  
  
    ```  
    get-sprsserviceapplication  
    ```  
  
3.  Следующий пример возвращает текущие значения модуля доставки электронной почты для приложения службы с именем «SSRS_TESTAPPLICATION».  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
    ```  
  
4.  Следующий пример создает новый файл с именем «emailconfig.txt», содержащий текущие значения модуля доставки электронной почты для приложения службы с именем «SSRS_TESTAPPLICATION».  
  
    ```  
    $app=get-sprsserviceapplication |where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml | out-file c:\emailconfig.txt  
    ```  
  
  
Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
