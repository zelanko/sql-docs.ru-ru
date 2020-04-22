---
title: Настройка использования альтернативного имени субъекта в Reporting Services | Документы Майкрософт
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 41a39c92a8ec9e9d940c44660a02abe5e710fede
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487027"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a>Настройка использования альтернативного имени субъекта в Reporting Services

В этом разделе объясняется, как настроить службы Reporting Services (SSRS) так, чтобы в них использовалось альтернативное имя субъекта (SAN), изменив файл rsreportserver.config и используя средство Netsh.exe.

Инструкции применяются к URL-адресу службы отчетов, а также URL-адресу веб-службы.

Чтобы использовать SAN, TLS/SSL-сертификат должен быть зарегистрирован на сервере, подписан и иметь закрытый ключ. Самозаверяющий сертификат использовать невозможно.  
  
 URL-адреса в службах Reporting Services можно настроить для использования TLS/SSL-сертификата. Обычно сертификат имеет только имя субъекта, которое позволяет ему использовать только один URL-адрес для сеанса TLS (ранее —SSL). SAN — это дополнительное поле в сертификате, которое позволяет службе TLS прослушивать множество URL-адресов, а также совместно использовать порт TLS с другими приложениями. SAN выглядит следующим образом: `www.s2.com`.  
  
 Дополнительные сведения о параметрах TLS для служб Reporting Services см. в разделе [Настройка соединений TLS для сервера отчетов, работающего в собственном режиме](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
## <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a>Настройка SSRS для использования альтернативного имени субъекта для URL-адреса веб-службы
  
1.  Запустите диспетчер конфигурации служб Reporting Services.  
  
     Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
2.  Выберите на странице **URL-адрес веб-службы** порт TLS/SSL и TLS/SSL-сертификат.  
  
     ![Диспетчер конфигурации служб Reporting Services](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "Диспетчер конфигурации служб Reporting Services")  
  
     Диспетчер конфигурации зарегистрирует TLS/SSL-сертификат для порта.  
  
3.  Откройте файл rsreportserver.config.  
  
     Файл для служб SSRS в собственном режиме находится в следующей папке по умолчанию:  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  Скопируйте раздел URL-адреса для приложения веб-службы сервера отчетов.  
  
     Например, следующий исходный раздел URL-адреса:  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     Следующий измененный раздел URL-адреса:
  
    ```  
    <URL>  
         <UrlString>https://www.s1.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.s2.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
5.  Сохраните файл rsreportserver.config.  
  
6.  Откройте командную строку от имени администратора и запустите средство Netsh.exe.  
  
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
    Reserved URL            : https:// www.s1.com:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)  
    ```  
  
     urlacl — это DACL (список управления доступом на уровне пользователей) для зарезервированного URL-адреса.  
  
9. Создайте альтернативное имя субъекта с тем же пользователем и SDDL как существующую запись, введя следующее.  
  
    ```  
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)  
  
    ```  
  
10. Щелкните на странице **Состояние сервера отчетов** диспетчера конфигурации Reporting Services кнопку **Остановить** , а затем нажмите **Запустить** , чтобы перезапустить сервер отчетов.  
  
## <a name="see-also"></a>См. также раздел

 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Диспетчер конфигурации служб Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Изменение файла конфигурации служб Reporting Services](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [Настройка URL-адресов сервера отчетов](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
