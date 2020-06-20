---
title: Служба Claims to Windows Token Service (C2WTS) и Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 72b88bd1bd2a033683f83dd53cca8404eccb613f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059349"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Служба Claims to Windows Token Service (C2WTS) и службы Reporting Services
  Служба SharePoint Claims to Windows Token Service (c2WTS) необходима в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режиме интеграции с SharePoint, если требуется использовать проверку подлинности Windows для источников данных, находящихся за пределами фермы SharePoint. Это верно, даже если пользователь получает доступ к источникам данных с использованием проверки подлинности Windows, поскольку для связи между клиентским веб-интерфейсом и общей службой [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] всегда используется проверка подлинности Claims.  
  
 Служба c2WTS необходима, даже если источники данных находятся на одном компьютере с общей службой. Однако в этом случае ограниченное делегирование не требуется.  
  
 Токены, созданные службой c2WTS, работают только при наличии ограниченного делегирования (ограничение набором определенных служб) и заданном параметре "Использовать любой протокол проверки подлинности". Как уже отмечалось, если источники данных находятся на одном компьютере с общей службой, ограниченное делегирование не требуется.  
  
 Если в среде используется делегирование, ограниченное Kerberos, то внешние источники данных и служба SharePoint Server должны находиться в одном домене Windows. Любая служба, использующая службу токенов Claims to Windows Service (c2WTS), должна применять делегирование, **ограниченное** Kerberos, чтобы разрешить c2WTS использовать передачу протокола Kerberos для перевода утверждений в учетные данные Windows. Эти требования являются достоверными для всех общих служб SharePoint. Дополнительные сведения см. в [статье Обзор проверки подлинности Kerberos для продуктов Microsoft https://technet.microsoft.com/library/gg502594.aspx) SharePoint 2010 (](https://technet.microsoft.com/library/gg502594.aspx).  
  
 Эта процедура описана в данном разделе.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
## <a name="prerequisites"></a>Предварительные требования  
  
> [!NOTE]  
>  Примечание. Некоторые шаги настройки могут отличаться или могут не работать в определенных топологиях фермы. Например, установка одиночного сервера не поддерживает службы c2WTS Windows Identity Foundation, поэтому в этой конфигурации фермы требования сценариев делегирования токенов Windows невозможны.  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>Основные шаги для настройки службы c2WTS  
  
1.  Настройка учетной записи службы c2WTS. Добавьте учетную запись службы к группе локальных администраторов на каждом сервере приложений с c2WTS. Кроме того, убедитесь, что учетная запись имеет следующие права локальной политики безопасности:  
  
    -   работа в качества части операционной системы;  
  
    -   олицетворение клиента после проверки подлинности;  
  
    -   Вход в систему в качестве службы.  
  
     Учетная запись, используемая для c2WTS, также должна быть настроена для ограниченного делегирования с переходом по протоколу и требует разрешений для делегирования службам, с которыми он должен взаимодействовать (т. е. SQL Server подсистеме SQL Server Analysis Services). Для настройки делегирования можно использовать оснастку Active Directory пользователи и компьютеры.  
  
    1.  Щелкните правой кнопкой мыши каждую учетную запись службы и откройте диалоговое окно свойств. В диалоговом окне перейдите на вкладку **Делегирование** .  
  
        > [!NOTE]  
        >  Примечание. Вкладка делегирования отображается, только если объекту назначено имя участника-службы. c2WTS не требует наличия имени субъекта-службы в учетной записи c2WTS, но без имени субъекта-службы, вкладка **делегирования** не будет отображаться. Другой способ настройки ограниченного делегирования заключается в использовании специальной программы, например **ADSIEdit**.  
  
    2.  Основными параметрами, приведенными на вкладке делегирования, являются следующие:  
  
        -   Установите флажок "доверять этому пользователю делегирование только указанных служб".  
  
        -   Выберите "использовать любой протокол проверки подлинности".  
  
         Дополнительные сведения см. в разделе "Настройка ограниченного делегирования Kerberos для компьютеров и учетных записей служб" в следующем техническом документе [Настройка проверки подлинности Kerberos для продуктов SharePoint 2010 и SQL Server 2008 R2](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products)  
  
2.  Настройка c2WTS "AllowedCallers"  
  
     c2WTS требует явного перечисления удостоверений "Calls" в файле конфигурации **c2wtshost.exe.config**. c2WTS не принимает запросы от всех пользователей, прошедших проверку подлинности в системе, если это не настроено. В этом случае вызывающим является группа Windows WSS_WPG. Файл c2wtshost.exe.confi хранится в следующем расположении:  
  
     **\Program Files\Windows Identity Foundation\v3.5\c2wtshost.exe.config**  
  
     В следующем примере показан файл конфигурации:  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```  
  
3.  Запустите службу c2WTS операционной системы:  
  
    1.  Задайте использование службой учетной записи, настроенной в предыдущем шаге.  
  
    2.  Измените тип запуска на "**автоматически**" и запустите службу.  
  
4.  Запустите SharePoint "Claims to Windows Token Service": запустите службу Claims to Windows Token Service через центр администрирования SharePoint на странице **Управление службами на сервере** . Служба должна быть запущена на сервере, который будет выполнять действие. Например, при наличии сервера, который является интерфейсным веб-сервером, и другого сервера, который служит сервером приложений, где работает общая служба служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , службу c2WTS необходимо запустить только на сервере приложений. Служба c2WTS не требуется на интерфейсном веб-сервере.  
  
## <a name="see-also"></a>См. также:  
 [Обзор службы Claims to Windows Token Service (c2WTS) (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx)   
 [Общие сведения о проверке подлинности Kerberos для продуктов Microsoft SharePoint 2010 (https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx)  
  
