---
title: "Настройка нестандартной проверки подлинности или проверки подлинности форм на сервере отчетов | Документы Microsoft"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Forms authentication, configuring
- custom authentication [Reporting Services]
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
caps.latest.revision: 20
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 325b7d6f1015b6e5e81565df37d1c02d20e5802f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="configure-custom-or-forms-authentication-on-the-report-server"></a>Настройка нестандартной проверки подлинности или проверку подлинности с помощью форм на сервере отчетов

Службы Reporting Services предоставляют открытую архитектуру, которая позволяет подключать нестандартные модули проверки подлинности и модули проверки подлинности с помощью форм. Можно рассмотреть возможность реализации нестандартного модуля проверки подлинности, если требования к развертыванию не включают встроенной безопасности Windows или обычную проверку подлинности. Наиболее распространенный сценарий использования нестандартной проверки подлинности — доступ к веб-приложению через Интернет или экстрасеть. Замена модуля проверки подлинности Windows по умолчанию нестандартным модулем проверки подлинности обеспечивает более широкие возможности управления предоставлением доступа к серверу отчетов внешним пользователям.  

На практике для развертывания нестандартного модуля проверки подлинности требуется выполнить несколько шагов, в том числе копировать сборки и файлы приложений, изменять файлы конфигурации и выполнять тестирование. В этом разделе рассматриваются только параметры проверки подлинности, указанные в файлах конфигурации.  

> [!NOTE]
>  Чтобы создать нестандартный модуль проверки подлинности, необходимо написать определенный код и хорошо разбираться в системе безопасности [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Если не нужно создавать нестандартный модуль проверки подлинности, можно использовать группы и учетные записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory, но это связано со значительным уменьшением области развертывания сервера отчетов. Дополнительные сведения о нестандартной проверке подлинности см. в разделе [Implementing a Security Extension](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md).

Кроме того Если вы хотите использовать проверку подлинности форм или нестандартный модуль проверки подлинности в среде SQL Server Reporting Services, интегрированных с продуктами SharePoint, необходимо настроить сайт SharePoint на использование выбранного метода проверки подлинности. Дополнительные сведения о настройке проверки подлинности в SharePoint см. в разделе [Authentication Samples](http://go.microsoft.com/fwlink/?LinkId=115575) в библиотеке MSDN [!INCLUDE[msCoName](../../includes/msconame-md.md)] .



### <a name="to-configure-a-report-server-to-use-custom-authentication"></a>Настройка сервера отчетов для использования нестандартной проверки подлинности

1.  Откройте файл конфигурации RSReportServer.config в текстовом редакторе.

2.  Найти \< **проверки подлинности**>.

3.  Скопируйте следующую структуру XML:

    ```
    <Authentication>
          <AuthenticationTypes>
                 <Custom />
          </AuthenticationTypes>
          <EnableAuthPersistence>true</EnableAuthPersistence>
    </Authentication>
    ```

4.  Вставьте его поверх существующих записей для \< **проверки подлинности**>.

     Следует заметить, что **Custom** нельзя использовать с другими типами проверки подлинности.

5.  Сохраните файл.

6.  Откройте файл конфигурации Web.config для сервера отчетов. По умолчанию он находится в \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer.

7.  Найдите параметр **authentication mode** и установите значение **Forms**.

    ```
    <authentication mode = "Forms" />
    ```

8.  Найдите параметр **identity impersonate** и установите значение **False**.

    ```
    <identity impersonate = "false" />  
    ```
9. Добавьте элемент структуры **PassThroughCookies** к файлу конфигурации. Дополнительные сведения см. в разделе [настроить веб-портал для передачи файлов cookie проверки подлинности пользовательского](../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)
  
10. Сохраните файл.  
  
11. Если настроено масштабное развертывание, повторите все предыдущие шаги для других серверов отчетов в развертывании.  
  
12. Перезапустите сервер отчетов, чтобы очистить все открытые сеансы.  

## <a name="see-also"></a>См. также:

[Реализация модуля безопасности](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)  
[Пользовательский модуль безопасности образец Reporting Services (GitHub)](https://github.com/Microsoft/Reporting-Services/tree/master/CustomSecuritySample)  
[Проверка подлинности с использованием сервера отчетов](../../reporting-services/security/authentication-with-the-report-server.md)   
[Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Настройка обычной проверки подлинности на сервере отчетов](../../reporting-services/security/configure-basic-authentication-on-the-report-server.md)   
[Настройка проверки подлинности Windows на сервере отчетов](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md)  
Дополнительные вопросы? [Повторите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
