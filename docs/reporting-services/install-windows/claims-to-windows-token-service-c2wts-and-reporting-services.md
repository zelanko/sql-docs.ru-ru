---
title: "Служба claims to Windows Token Service (c2WTS) и службы Reporting Services | Документы Microsoft"
ms.custom: The Claims to Windows Token Service (C2WTS) is used by SharePoint and needs to be configured for Kerberos constrained delegation to work with SQL Server Reporting Services properly.
ms.date: 09/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a9397f427cac18d0c8bfc663f6bd477b0440b8a3
ms.openlocfilehash: 8a478bba3cde66967594d5ef02f867de5b33edd7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/15/2017

---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Служба Claims to Windows Token Service (C2WTS) и службы Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Служба SharePoint Claims to Windows Token Service (C2WTS) является обязательным, если для просмотра отчетов в собственном режиме в пределах [веб-часть для просмотра отчетов служб отчетов SQL Server](../report-server-sharepoint/deploy-report-viewer-web-part.md).

C2WTS также является обязательным в режиме SQL Server Reporting Services SharePoint, если вы хотите использовать проверку подлинности Windows для источников данных, которые находятся за пределами фермы SharePoint. Служба C2WTS необходима, даже если источники данных находятся на одном компьютере с общей службой. Однако в этом случае ограниченное делегирование не требуется.

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступны после SQL Server 2016.

## <a name="report-viewer-web-part-configuration"></a>Настройка веб-частей для средства просмотра отчетов

Веб-часть средства просмотра отчетов можно использовать для внедрения отчетов служб SQL Server Reporting Services в собственном режиме на сайте SharePoint. Этот веб-части для SharePoint 2013 и SharePoint 2016. SharePoint 2013 и SharePoint 2016 сделать использование проверки подлинности утверждений. SQL Server Reporting Services (собственный режим) по умолчанию используется проверка подлинности Windows. В результате C2WTS должна быть настроена правильно для отчетов к просмотру правильно.

## <a name="sharepoint-mode-integaration"></a>Integaration режим SharePoint

**Этот раздел относится только к SQL Server 2016 Reporting Services и более ранних версий.**

Служба SharePoint Claims to Windows Token Service (C2WTS) требуется в режиме SQL Server Reporting Services SharePoint, если вы хотите использовать проверку подлинности Windows для источников данных, которые находятся за пределами фермы SharePoint. Это верно, даже если пользователь обращается к источникам данных с проверкой подлинности Windows, так как обмен данными между веб-интерфейса (WFE) и общей службы Reporting Services всегда используется проверка подлинности Claims.

## <a name="steps-needed-to-configure-c2wts"></a>Шаги, необходимые для настройки службы c2WTS

Токены, созданные службой C2WTS, работают только при наличии ограниченного делегирования (ограничение набором определенных служб) и установленном параметре «Использовать любой протокол проверки подлинности». Как уже отмечалось, если источники данных находятся на одном компьютере с общей службой, ограниченное делегирование не требуется.

Если в среде используется делегирование, ограниченное Kerberos, то внешние источники данных и служба SharePoint Server должны находиться в одном домене Windows. Любая служба, использующая службу токенов Claims to Windows Service (c2WTS), должна применять делегирование, **ограниченное** Kerberos, чтобы разрешить c2WTS использовать передачу протокола Kerberos для перевода утверждений в учетные данные Windows. Эти требования являются достоверными для всех общих служб SharePoint. Дополнительные сведения см. в разделе [Планирование проверки подлинности Kerberos в SharePoint 2013](http://technet.microsoft.com/library/ee806870.aspx).  

1. Настройка учетной записи службы C2WTS. Добавьте учетную запись службы к группе локальных администраторов на каждом сервере, что будет использоваться C2WTS.

    Для **веб-части средства просмотра отчетов**, это будет серверов Web Front End (WFE). Для **режиме интеграции с SharePoint**, это будет серверов приложений, где запущена служба Reporting Services.

2. Настройка делегирования для учетной записи службы C2WTS.

    Учетной записи необходимо настроить ограниченное делегирование со сменой протоколов и разрешения на делегирование для служб, с которыми он необходим для взаимодействия с (т. е. SQL Server Database Engine, SQL Server Analysis Services). Для настройки делегирования можно использовать оснастку «Active Directory-пользователи и компьютеры» и должен быть администратором домена.

    > [!IMPORTANT]
    > Необходимые параметры следует настроить учетной записи службы C2WTS на вкладке делегирования, должна соответствовать основной учетной записи службы. Для **веб-части средства просмотра отчетов**, это будет учетная запись службы для веб-приложения SharePoint. Для **режиме интеграции с SharePoint**, это будет учетная запись службы Reporting Services.
    >
    > Например если разрешить учетной записи службы C2WTS делегировать службы SQL, необходимо сделать это в учетной записи службы Reporting Services в режиме интеграции с SharePoint.

    * Щелкните правой кнопкой мыши каждую учетную запись службы и откройте диалоговое окно свойств. В диалоговом окне перейдите на вкладку **Делегирование** .

        Вкладка делегирования отображается только в том случае, если объекту назначено имя участником службы (SPN). Службе C2WTS не требуется имени участника-службы для учетной записи службы C2WTS, однако без имени участника-службы **делегирования** вкладки не будут видны. Другой способ настройки ограниченного делегирования заключается в использовании специальной программы, например **ADSIEdit**.

    * Основными параметрами, приведенными на вкладке делегирования, являются следующие:

        * Выберите **доверять этому пользователю делегирование указанных служб**
        * Выберите **использовать любой протокол проверки подлинности**

    * Выберите **Добавить** , чтобы добавить службу, которая является адресатом делегирования.

    * Выберите **пользователи или компьютеры... *** и введите учетную запись, на котором размещена служба. Например, если SQL Server выполняется под учетной записью с именем *sqlservice*, введите `sqlservice`. 

    * Выберите список служб. Отобразятся имена участников-служб, которые доступны в этой учетной записи. Если вы не видите в списке службу для соответствующей учетной записи, возможно, она отсутствует или размещена в другой учетной записи. Для настройки имен SPN можно использовать служебную программу SetSPN.

    * Нажмите кнопку ОК, чтобы закрыть все диалоговые окна.

3. Настройки службы C2WTS *AllowedCallers*.

    Службы C2WTS требуется удостоверения «вызывающим объектам», явно перечисленные в файле конфигурации **C2WTShost.exe.config**. Служба C2WTS принимает запросы от всех пользователей системы, прошедших проверку подлинности, только если она настроена на это. В этом случае вызывающий является группа WSS_WPG Windows. Файл c2wtshost.exe.confi хранится сохраняются в следующем расположении:

    Изменение учетной записи службы в центре администрирования SharePoint (для службы C2WTS) добавит эту учетную запись в группу WSS_WPG.

    **\Program Files\Windows Identity Foundation\v3.5\c2WTShost.exe.config**

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

4. Запустите службу Claims to Windows Token Service через Центр администрирования SharePoint на **управление службами на сервере** страницы. Служба должна быть запущена на сервере, который будет выполнять действие. Например, при наличии сервера, то есть WFE и другого сервера, сервера приложений с общей службы SQL Server Reporting Services работает, только необходимо запустить C2WTS на сервере приложений. C2WTS требуется только на веб-сервере, если вы используете веб-части средства просмотра отчетов.

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
