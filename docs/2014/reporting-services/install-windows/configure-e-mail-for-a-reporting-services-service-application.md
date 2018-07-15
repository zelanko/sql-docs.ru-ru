---
title: Настройка электронной почты для приложения службы (SharePoint 2010 и SharePoint 2013) служб Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5432b0d2fa1c5fd7504b4706fb85b240efeb9c34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236224"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a>Настройка электронной почты для приложения служб Reporting Services (SharePoint 2010 и SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Функция предупреждения об изменении данных служб отправляет предупреждения в сообщениях электронной почты. Для отправки электронной почты могут потребоваться настройка приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и изменение модуля доставки электронной почты приложением службы. Необходимо настроить параметры электронной почты и в том случае, если планируется использование модуля доставки электронной почты функцией подписки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint &#124; SharePoint 2010 и SharePoint 2013.|  
  
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
  
1.  Если среда электронной почты требует проверки подлинности NTLM и не поддерживает анонимный доступ, необходимо изменить настройки модуля доставки электронной почты приложениям службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Укажите для параметра **SMTPAuthenticate** значение «2». Это значение нельзя изменить через пользовательский интерфейс. Следующий пример скрипта PowerShell обновляет полную конфигурацию расширения сервера отчетов для доставки электронной почты приложением службы с именем «SSRS_TESTAPPLICATION». Обратите внимание, что некоторые перечисленные в скрипте узлы (например, адрес отправителя) можно также задать через пользовательский интерфейс.  
  
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
  
  
