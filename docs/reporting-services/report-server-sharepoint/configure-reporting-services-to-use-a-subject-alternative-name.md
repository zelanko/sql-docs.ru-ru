---
title: Настройка использования альтернативного имени субъекта в Reporting Services (SAN) | Документы Майкрософт
description: Узнайте, как настроить службы SQL Server Reporting Services и Сервер отчетов Power BI так, чтобы в них использовалось альтернативное имя субъекта (SAN), изменив файл rsreportserver.config и используя средство Netsh.exe.
ms.date: 09/27/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 40ddab224d24e566ad346d64d5238ca5c81d9f48
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891594"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name-san"></a>Настройка использования альтернативного имени субъекта в Reporting Services (SAN)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

В этом разделе объясняется, как настроить службы Reporting Services (SSRS) и Сервер отчетов Power BI так, чтобы в них использовалось альтернативное имя субъекта (SAN), изменив файл rsreportserver.config и используя средство Netsh.exe.

Эти инструкции относятся к URL-адресу веб-службы, а также к URL-адресу веб-портала в средстве Configuration Manager сервера отчетов.

Чтобы использовать SAN, TLS/SSL-сертификат должен быть зарегистрирован на сервере, подписан и иметь закрытый ключ. Самозаверяющий сертификат использовать невозможно.

URL-адреса в Reporting Services и Сервере отчетов Power BI можно настроить на использование сертификата TLS/SSL. Обычно сертификат имеет только имя субъекта, которое позволяет ему использовать только один URL-адрес для сеанса TLS (ранее —SSL). SAN — это дополнительное поле в сертификате, которое позволяет службе TLS прослушивать множество URL-адресов, а также совместно использовать порт TLS с другими приложениями. Например, SAN может быть похожим на `www.myreports.com`.

Дополнительные сведения о параметрах TLS для служб Reporting Services см. в разделе [Настройка соединений TLS для сервера отчетов, работающего в собственном режиме](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
## <a name="configure-to-use-a-subject-alternative-name-for-web-service-url"></a>Настройка для использования альтернативного имени субъекта для URL-адреса веб-службы
  
1.  Запустите диспетчер конфигурации Configuration Manager сервера отчетов.  
  
     Дополнительные сведения см. в разделе [Диспетчер конфигурации сервера отчетов (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
2.  Выберите на странице **URL-адрес веб-службы** порт TLS/SSL и TLS/SSL-сертификат.  
  
     ![Диспетчер конфигурации сервера отчетов](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Диспетчер конфигурации сервера отчетов")  
  
     Диспетчер конфигурации зарегистрирует TLS/SSL-сертификат для порта.  
  
3.  Откройте файл rsreportserver.config.  
  
     Файл для служб SSRS 2016 в собственном режиме находится в следующей папке по умолчанию:  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
     Файл для служб SSRS 2017 и более поздней версии находится в следующей папке по умолчанию:  
  
    ```  
    \Program Files\Microsoft SQL Server Reporting Services\SSRS\ReportServer  
    ```  
    
     Файл для Сервера отчетов Power BI находится в следующей папке по умолчанию:  
  
    ```  
    \Program Files\Microsoft Power BI Report Server\PBIRS\ReportServer  
    ```  
  
4.  Скопируйте раздел URL-адреса для приложения **ReportServerWebService**.
  
     Например, следующий исходный раздел URL-адреса:  
  
    ```  
        <URL>  
         <UrlString>https://+:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051</AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
  
    ```  
  
     Следующий измененный раздел URL-адреса:
  
    ```  
    <URL>  
         <UrlString>https://+:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051</AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.myreports.com:443</UrlString>  
         <AccountSid>S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051/AccountSid>  
         <AccountName>NT Service\ReportServer</AccountName>  
        </URL>  
  
    ```  
  
  > [!TIP]  
>  * Для SSRS 2017 и более поздних версий значение `AccountSid` составляет `S-1-5-80-4050220999-2730734961-1537482082-519850261-379003301`, а значение `AccountName` — `NT SERVICE\SQLServerReportingServices`.
>  * Для Сервера отчетов Power BI значение `AccountSid` составляет `S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663`, а значение `AccountName` — `NT SERVICE\PowerBIReportServer`.
  
5.  Сохраните файл rsreportserver.config.  
  
6.  Откройте командную строку от **имени администратора** и запустите средство Netsh.exe.  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  Переключитесь в контекст HTTP, введя следующее.  
  
    ```  
    Netsh>http  
    ```  
  
8.  Отобразите существующие urlacl, введя следующее:
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     Появится запись, аналогичная следующей.  
  
    ```  
    Reserved URL            : https://+:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
    ```  
  
     urlacl — это DACL (список управления доступом на уровне пользователей) для зарезервированного URL-адреса.  
  
9. Создайте альтернативное имя субъекта с тем же пользователем и SDDL как существующую запись, введя следующее.  
  
    ```  
    netsh http>add urlacl  url=https://www.myreports.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
  
    ```  
  
10. Для **URL-адреса веб-портала**создайте новую запись для альтернативного имени субъекта, введя следующее:

    ```  
    netsh http>add urlacl  url=https://www.myreports.com:443/Reports  
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-2885764129-887777008-271615777-1616004480-2722851051)  
  
    ```  
> [!TIP]  
>  * Для SSRS 2017 и более поздних версий значение `user` составляет `NT SERVICE\SQLServerReportingServices`, а значение `sddl` — `D:(A;;GX;;;S-1-5-80-4050220999-2730734961-1537482082-519850261-379003301)`.
>  * Для Сервера отчетов Power BI значение `user` составляет `NT SERVICE\PowerBIReportServer`, а значение `sddl` — `S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663`.

> [!NOTE]  
> Для Сервера отчетов Power BI необходимо создать две дополнительные записи для альтернативного имени субъекта, введя следующее:
>  * `add urlacl url=https://www.myreports.com:443/PowerBI user="NT SERVICE\PowerBIReportServer" sddl=D:(A;;GX;;;S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663)`
>  * `add urlacl url=https://www.myreports.com:443/wopi user="NT SERVICE\PowerBIReportServer" sddl=D:(A;;GX;;;S-1-5-80-1730998386-2757299892-37364343-1607169425-3512908663)`

11. Щелкните на странице **Состояние сервера отчетов** диспетчера конфигурации сервера отчетов кнопку **Остановить**, а затем нажмите **Запустить**, чтобы перезапустить сервер отчетов.  
  
## <a name="see-also"></a>См. также раздел

 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Диспетчер конфигурации сервера отчетов](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Изменение файла конфигурации служб Reporting Services](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [Настройка URL-адресов сервера отчетов](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
