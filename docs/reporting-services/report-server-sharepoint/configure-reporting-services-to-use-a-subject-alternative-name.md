---
title: "Настройка служб Reporting Services для использования альтернативного имени субъекта | Документы Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 73f48b2978055481f1ee93952fb3a35eb84ec416
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a>Настройка служб Reporting Services для использования альтернативного имени субъекта

В этом разделе описывается Настройка Reporting Services (SSRS) для использования альтернативного имени субъекта (SAN), изменив файл rsreportserver.config и используя средство Netsh.exe.

Инструкции применяются к URL-адресу службы отчетов, а также URL-адресу веб-службы.

Чтобы использовать SAN, SSL-сертификат должен быть зарегистрирован на сервере, подписан и иметь закрытый ключ. Самозаверяющий сертификат использовать невозможно.  
  
 URL-адреса в службах Reporting Services можно настроить для использования сертификата SSL. Обычно сертификат имеет только имя субъекта, которое позволяет ему использовать только один URL-адрес для сеанса SSL. SAN — это дополнительное поле в сертификате, которое позволяет службе SSL прослушивать многих URL-адресов и совместно использовать порт SSL с другими приложениями. SAN выглядит `www.s2.com`.  
  
 Дополнительные сведения о параметрах протокола SSL для служб Reporting Services см. в разделе [Настройка соединений SSL для сервера отчетов в собственном режиме](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
## <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a>Настройка SSRS для использования альтернативного имени субъекта для URL веб-службы
  
1.  Запустите диспетчер конфигурации служб Reporting Services.  
  
     Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
2.  Выберите на странице **URL-адрес веб-службы** порт SSL и SSL-сертификат.  
  
     ![Диспетчер конфигурации служб Reporting Services](../../reporting-services/report-server-sharepoint/media/reportingservices-configurationmanager.png "диспетчер конфигурации служб Reporting Services")  
  
     Диспетчер конфигурации зарегистрирует SSL-сертификат для порта.  
  
3.  Откройте файл rsreportserver.config.  
  
     Для служб SSRS в собственном режиме файл расположен в папке по умолчанию:  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  Скопируйте раздел URL-адреса для приложения веб-службы сервера отчетов.  
  
     Например следующий исходный раздел URL-адрес будет:  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     Имеет следующий измененный раздел URL-адрес:
  
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
  
## <a name="see-also"></a>См. также:

 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Диспетчер конфигурации служб Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Изменение файла конфигурации служб Reporting Services](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)   
 [Настройка URL-адресов сервера отчетов](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).

