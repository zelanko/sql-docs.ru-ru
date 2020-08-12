---
title: Настройка проверки подлинности Windows на сервере отчетов | Документы Майкрософт
ms.date: 06/22/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [Reporting Services]
- Reporting Services, configuration
ms.assetid: 4de9c3dd-0ee7-49b3-88bb-209465ca9d86
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c3320851b253b8ca509b564405db4b873e5dea0b
ms.sourcegitcommit: 4fe7b0d5e8ef1bc076caa3819f7a7b058635a486
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85263839"
---
# <a name="configure-windows-authentication-on-the-report-server"></a>Настройка проверки подлинности Windows на сервере отчетов
  По умолчанию службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] принимают запросы, в которых определена проверка подлинности Negotiate или NTLM. Если в развертывание входят клиентские приложения и браузеры, в которых используются поставщики безопасности, то можно использовать значения по умолчанию без дополнительной настройки. Если нужно использовать другого поставщика безопасности для встроенной безопасности Windows (например, требуется применять протокол Kerberos напрямую) или если значения по умолчанию были изменены, и нужно восстановить первоначальные настройки, то можно использовать сведения данного раздела, чтобы указать настройки проверки подлинности на сервере отчетов.  
  
 Чтобы использовать встроенную безопасность Windows, каждый пользователь, обращающийся к серверу отчетов, должен иметь правильную локальную или доменную учетную запись Windows или входить в локальную или доменную группу Windows. В группу можно включать учетные записи, относящиеся к другим доменам, если эти домены являются доверенными. Учетные записи должны иметь доступ к компьютеру, на котором размещен сервер отчетов. Впоследствии учетным записям нужно назначить роли, чтобы обеспечить им доступ к специфическим операциям сервера отчетов.  
  
 Должны выполняться также следующие дополнительные условия.  
  
-   Атрибуту **AuthenticationType** файлов RSReportServer.config должно быть присвоено значение **RSWindowsNegotiate**, **RSWindowsKerberos** или **RSWindowsNTLM**. По умолчанию файл конфигурации RSReportServer.config включает настройку **RSWindowsNegotiate** , если учетной записью службы сервера отчетов является учетная запись NetworkService или LocalSystem. В противном случае используется настройка **RSWindowsNTLM** . Можно добавить **RSWindowsKerberos** , если имеются приложения, в которых используется только проверка подлинности протокола Kerberos.  
  
    > [!IMPORTANT]  
    >  Использование **RSWindowsNegotiate** приведет к ошибке проверки подлинности протокола Kerberos, если служба сервера отчетов настроена на запуск с доменной учетной записью пользователя и для учетной записи не зарегистрировано имя участника-службы (SPN). Дополнительные сведения см. в разделе [Разрешение ошибок проверок подлинности протокола Kerberos при соединении с сервером отчетов](#proxyfirewallRSWindowsNegotiate) в этом разделе.  
  
-   [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] должна быть настроена для проверки подлинности Windows. По умолчанию файлы Web.config для веб-службы сервера отчетов содержат параметр \<authentication mode="Windows">. Если изменить его на \<authentication mode="Forms">, проверка подлинности Windows для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] завершится ошибкой.  
  
-   Файлы Web.config для веб-службы сервера отчетов должны содержать параметр \<identity impersonate= "true" />.  
  
-   Клиентское приложение или браузер должны поддерживать встроенную безопасность Windows.  

- [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] дополнительная настройка не требуется.
  
 Чтобы изменить настройки проверки подлинности сервера отчетов, измените XML-элементы и значения в файле RSReportServer.config. Чтобы реализовать определенные сочетания, можно копировать и вставить примеры из этого раздела.  
  
 Настройки по умолчанию работают лучше всего, если клиентский и серверный компьютер находятся в одном и том же домене или в доверенном домене, а сервер отчетов разворачивается для доступа из внутренней сети, защищенной корпоративным брандмауэром. Для передачи учетных данных Windows необходимо использовать доверенные и одиночные домены. Учетные данные можно передавать несколько раз в том случае, если для серверов включен протокол Kerberos версии 5. В противном случае учетные данные можно передать только один раз до истечения срока их действия. Дополнительные сведения о настройке учетных данных для нескольких подключений к компьютерам см. в разделе [Задание учетных данных и сведений о соединении для источников данных отчета](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
 Следующие параметры настраиваются для сервера отчетов, работающего в собственном режиме. Если развертывание сервера отчетов производилось в режиме интеграции с SharePoint, то необходимо пользоваться настройками проверки подлинности по умолчанию, в которых задана встроенная безопасность Windows. Сервер отчетов использует внутренние функции модуля проверки подлинности Windows по умолчанию для поддержки серверов отчетов в режиме интеграции с SharePoint.  
  
## <a name="extended-protection-for-authentication"></a>Расширенная защита для проверки подлинности  
 Начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], доступна поддержка расширенной защиты для проверки подлинности. Функция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует привязку каналов и служб для повышения уровня защиты проверки подлинности. Функции [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно использовать в ОС, поддерживающей расширенную защиту. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] определяется параметрами в файле RSReportServer.config. Это можно сделать как в текстовом редакторе, так и при помощи средств WMI API. Дополнительные сведения см. в статье [Extended Protection for Authentication with Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md).  
  
### <a name="to-configure-a-report-server-to-use-windows-integrated-security"></a>Настройка сервера отчетов на использование встроенной безопасности Windows  
  
1.  Откройте файл конфигурации RSReportServer.config в текстовом редакторе.  
  
2.  Найдите параметр \<**Authentication**>.  
  
3.  Выберите и скопируйте наиболее подходящую из следующих XML-структур. **RSWindowsNegotiate**, **RSWindowsNTLM**и **RSWindowsKerberos** можно указывать в любом порядке. Включите сохраняемость проверки подлинности, если нужно проверить подлинность соединений, а не каждого отдельного запроса. При сохраняемости проверки подлинности все запросы, для которых требуется проверка подлинности, разрешены в продолжение существования соединения.  
  
     Первая XML-структура является настройкой по умолчанию, если учетной записью службы сервера отчетов является учетная запись NetworkService или LocalSystem:  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     Вторая XML-структура является настройкой по умолчанию, если учетной записью службы сервера отчетов не является учетная запись NetworkService или LocalSystem:  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    ```  
  
     \</Authentication>  
  
     Третья XML-структура указывает все пакеты безопасности, используемые во встроенной безопасности Windows:  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
                 <RSWindowsKerberos />  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
     Четвертая XML-структура задает NTLM только для развертываний, которые не поддерживают протокол Kerberos или обходят ошибки проверки подлинности протокола Kerberos:  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
4.  Вставьте его на место существующих элементов \<**Authentication**>.  
  
     Также невозможно использование синтаксиса **Custom** с типами **RSWindows** .  
  
5.  При необходимости измените параметры расширенной защиты. По умолчанию расширенная защита отключена.  Если эти записи отсутствуют, возможно, на компьютере не установлена версия служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с поддержкой расширенной защиты. Дополнительные сведения см. в разделе [Extended Protection for Authentication with Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md).  
  
    ```  
          <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>  
          <RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
    ```  
  
6.  Сохраните файл.  
  
7.  Если настроено масштабное развертывание, повторите вышеперечисленные шаги для остальных серверов отчетов, входящих в конфигурацию развертывания.  
  
8.  Перезапустите сервер отчетов, чтобы очистить все открытые сеансы.  
  
##  <a name="resolving-kerberos-authentication-errors-when-connecting-to-a-report-server"></a><a name="proxyfirewallRSWindowsNegotiate"></a> Устранение ошибки проверки подлинности Kerberos, при соединении с сервером отчетов  
 На сервере отчетов, настроенном для проверки подлинности протоколов Negotiate или Kerberos, клиентское соединение с сервером отчетов завершится неудачей в случае ошибки проверки подлинности Kerberos. Известно, что ошибки проверки подлинности протокола Kerberos происходят вследствие следующих причин.  
  
-   Служба сервера отчетов выполняется с доменной учетной записью пользователя Windows, и для учетной записи не зарегистрировано имя участника-службы (SPN).  
  
-   Сервер отчетов настроен на режим **RSWindowsNegotiate** .  
  
-   Браузер выбирает протокол Kerberos вместо NTLM в заголовке проверки подлинности в запросе, посылаемом серверу отчетов.  
  
 Можно заметить ошибку, если включить ведение журнала протокола Kerberos. Другой признак ошибки — многократное получение запроса для ввода учетных данных с последующим появлением пустого окна браузера.  
  
 Наличие ошибки проверки подлинности протокола Kerberos можно подтвердить, удалив <**RSWindowsNegotiate**/> из файла конфигурации и повторив попытку соединения.  
  
 Если неполадка подтверждается, ее можно устранить следующими способами:  
  
-   Зарегистрируйте имя участника-службы для службы сервера отчетов, которая запускается от учетной записи пользователя домена. Дополнительные сведения см. в статье [Регистрация имени субъекта-службы (SPN) для сервера отчетов](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
-   Измените учетную запись службы для запуска под встроенной учетной записью, такой как сетевая служба. Встроенные учетные записи сопоставляют имя участника-службы HTTP с именем участника-службы Host, которое определяется при соединении компьютера с сетью. Дополнительные сведения см. в разделе [Настройка учетной записи службы (диспетчер конфигураций служб SSRS)](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).
  
-   Используйте NTLM. Как правило, NTLM функционирует в случаях, когда проверка подлинности протокола Kerberos заканчивается неуспешно. Чтобы задействовать NTLM, удалите **RSWindowsNegotiate** из файла RSReportServer.config и проверьте, что указан только **RSWindowsNTLM** . Если выбран этот подход, то можно продолжить использовать учетную запись пользователя домена для службы сервера отчетов, даже если для него не определено имя участника-службы (SPN).  
  
#### <a name="logging-information"></a>Информация в журнале  
 Имеется несколько источников информации, включаемой в журнал, которые могут помочь в решении проблем, связанных с протоколом Kerberos.  
  
##### <a name="user-account-control-attribute"></a>Атрибут управления учетными записями  
 Определите, задан ли необходимый атрибут учетной записи служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в Active Directory. Просмотрите файл журнала трассировки служб Reporting Services и найдите значение записи для атрибута управления учетными записями. Значение записи приведено в десятичном формате. Необходимо преобразовать десятичное значение в шестнадцатеричный формат и найти его в разделе MSDN, где описан атрибут управления учетными записями.  
  
-   Журнал трассировки служб Reporting Services будет выглядеть примерно следующим образом:  
  
    ```  
    appdomainmanager!DefaultDomain!8f8!01/14/2010-14:42:28:: i INFO: The UserAccountControl value for the service account is 590336  
    ```  
  
-   Например, десятичное значение можно преобразовать в шестнадцатеричный формат с помощью калькулятора [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Калькулятор поддерживает несколько режимов, где имеются переключатели «Dec» и «Hex». Установите переключатель в положение «Dec», вставьте или введите десятичное значение из файла журнала и переведите переключатель в положение «Hex».  
  
-   Откройте раздел [Атрибут управления учетными записями](https://go.microsoft.com/fwlink/?LinkId=183366) , чтобы получить атрибут для учетной записи службы.  
  
##### <a name="spns-configured-in-active-directory-for-the-reporting-services-service-account"></a>Имена участников-служб, настроенные в Active Directory для учетной записи служб Reporting Services  
 Чтобы включить имя участника зеркального отображения в файл журнала трассировки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , можно временно включить функцию расширенной защиты [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Внесите изменения в файл конфигурации **rsreportserver.config** , задав следующие параметры:  
  
    ```  
    <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>   
    <RSWindowsExtendedProtectionScenario>Any</RSWindowsExtendedProtectionScenario>  
    ```  
  
-   Перезапустите службу [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

 Если дальнейшей необходимости в использовании расширенной защиты нет, восстановите параметры по умолчанию и перезапустите учетную запись службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
```  
<RSWindowsExtendedProtectionLevel>Off</RSWindowsExtendedProtectionLevel>  
<RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
```  
  
 Дополнительные сведения см. в разделе [Extended Protection for Authentication with Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md).  
  
#### <a name="how-the-browser-chooses-negotiated-kerberos-or-negotiated-ntlm"></a>Как браузер выбирает Negotiated Kerberos или Negotiated NTLM  
 При использовании браузера Internet Explorer для подключения к серверу отчетов, он указывает Negotiated Kerberos или NTLM в заголовке проверки подлинности. NTLM используется вместо протокола Kerberos, когда:  
  
-   Запрос передан в локальный сервер отчетов.  
  
-   Запрос передан по IP-адресу компьютера сервера отчетов вместо заголовка узла или имени сервера.  
  
-   Программа брандмауэра блокирует порты, используемые для проверки подлинности протокола Kerberos.  
  
-   Протокол Kerberos не включен в операционной системе конкретного сервера.  
  
-   Домен содержит старые версии клиентских и серверных операционных систем Windows, которые не поддерживают проверку подлинности протокола Kerberos, встроенную в новые версии операционной системы.  
  
 Кроме того, Internet Explorer может выбрать Negotiated Kerberos или NTLM в зависимости от настроек URL-адреса, ЛВС и прокси-сервера.  
  
###### <a name="report-server-url"></a>URL-адрес сервера отчетов  
 Если URL-адрес содержит полное доменное имя, то Internet Explorer выбирает NTLM. Если URL-адрес указывает localhost, то Internet Explorer выбирает NTLM. Если URL-адрес указывает сетевое имя компьютера, то Internet Explorer выбирает Negotiate, и успех или неудача зависит от существования имени участника-службы (SPN) для учетной записи службы сервера отчетов.  
  
###### <a name="lan-and-proxy-settings-on-the-client"></a>Настройки локальной сети и прокси-сервера на клиенте  
 Настройки локальной сети и прокси-сервера, установленные в браузере Internet Explorer, могут определить выбор NTLM вместо протокола Kerberos. Но поскольку настройки локальной сети и прокси-сервера различны в пределах организации, невозможно точно определить настройки, которые привели к ошибкам проверки подлинности протокола Kerberos. Например, в организации могут принудительно применяться настройки прокси-сервера, которые преобразуют URL-адреса из URL-адресов интрасети в URL-адреса полного доменного имени, разрешаемые через интернет-соединения. Если для различных типов URL-адресов используются разные поставщики проверки подлинности, то некоторые соединения могут оказаться успешными вопреки ожиданиям.  
  
 Если возникают ошибки соединения, которые можно объяснить сбоями проверки подлинности, можно применить различные сочетания настройки локальной сети и прокси-сервера, чтобы обнаружить проблему. В Internet Explorer настройки локальной сети и прокси-сервера находятся в диалоговом окне **Настройки локальной сети** , которое можно открыть, нажав кнопку **Настройки LAN** на вкладке **Подключения** окна **Свойства: Интернет**.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Дополнительные сведения о Kerberos и серверах отчетов см. на странице [Развертывание решений бизнес-аналитики с помощью SharePoint, служб Reporting Services и сервера мониторинга PerformancePoint с Kerberos.](https://go.microsoft.com/fwlink/?LinkID=177751)  
  
## <a name="see-also"></a>См. также:  
 [Проверка подлинности с использованием сервера отчетов](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Предоставление разрешений на сервер отчетов в собственном режиме](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Настройка обычной проверки подлинности на сервере отчетов](../../reporting-services/security/configure-basic-authentication-on-the-report-server.md)   
 [Настройка нестандартной проверки подлинности или проверку подлинности с помощью форм на сервере отчетов](../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md)   
 [Extended Protection for Authentication with Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)  
  
  
