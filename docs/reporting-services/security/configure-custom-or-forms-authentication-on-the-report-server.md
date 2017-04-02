---
title: "Настройка нестандартной проверки подлинности или проверку подлинности с помощью форм на сервере отчетов | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Проверка подлинности на основе форм, настройка"
  - "нестандартная проверка подлинности [службы Reporting Services]"
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 16
---
# Настройка нестандартной проверки подлинности или проверку подлинности с помощью форм на сервере отчетов
  Службы Reporting Services предоставляют открытую архитектуру, которая позволяет подключать нестандартные модули проверки подлинности и модули проверки подлинности с помощью форм. Можно рассмотреть возможность реализации нестандартного модуля проверки подлинности, если требования к развертыванию не включают встроенной безопасности Windows или обычную проверку подлинности. Наиболее распространенный сценарий использования нестандартной проверки подлинности — доступ к веб-приложению через Интернет или экстрасеть. Замена модуля проверки подлинности Windows по умолчанию нестандартным модулем проверки подлинности обеспечивает более широкие возможности управления предоставлением доступа к серверу отчетов внешним пользователям.  
  
 На практике для развертывания нестандартного модуля проверки подлинности требуется выполнить несколько шагов, в том числе копировать сборки и файлы приложений, изменять файлы конфигурации и выполнять тестирование. В этом разделе рассматриваются только параметры проверки подлинности, указанные в файлах конфигурации.  
  
> [!NOTE]  
>  Чтобы создать нестандартный модуль проверки подлинности, необходимо написать определенный код и хорошо разбираться в системе безопасности [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Если не нужно создавать нестандартный модуль проверки подлинности, можно использовать группы и учетные записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory, но это связано со значительным уменьшением области развертывания сервера отчетов. Дополнительные сведения о нестандартной проверке подлинности см. в разделе [Implementing a Security Extension](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md).  
  
 Кроме того, если нужно использовать проверку подлинности с помощью форм или нестандартный модуль проверки подлинности в среде служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , интегрированной с продуктом SharePoint, то необходимо настроить сайт SharePoint на использование выбранного метода проверки подлинности. Дополнительные сведения о настройке проверки подлинности в SharePoint см. в разделе [Authentication Samples](http://go.microsoft.com/fwlink/?LinkId=115575) в библиотеке MSDN [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
### Настройка сервера отчетов для использования нестандартной проверки подлинности  
  
1.  Откройте файл конфигурации RSReportServer.config в текстовом редакторе.  
  
2.  Найдите параметр \<**проверка подлинности**>.  
  
3.  Скопируйте следующую структуру XML:  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  Вставьте ее на место существующих элементов параметра \<**проверка подлинности**>.  
  
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
  
9. Откройте файл конфигурации Web.config для диспетчера отчетов. По умолчанию она находится в каталоге «\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager».  
  
10. Найдите параметр **authentication mode** и установите значение **Forms**.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. Найдите параметр **identity impersonate** и установите значение **False**.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. Добавьте элемент структуры **PassThroughCookies** к файлу конфигурации. Дополнительные сведения см. в разделе [Настройка передачи куки-файлов для нестандартной проверки подлинности пользователя в диспетчере отчетов](../Topic/Configure%20Report%20Manager%20to%20Pass%20Custom%20Authentication%20Cookies.md).  
  
13. Сохраните файл.  
  
14. Если настроено масштабное развертывание, повторите все предыдущие шаги для других серверов отчетов в развертывании.  
  
15. Перезапустите сервер отчетов, чтобы очистить все открытые сеансы.  
  
## См. также  
 [Реализация модуля безопасности](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)   
 [Проверка подлинности с использованием сервера отчетов](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Настройка обычной проверки подлинности на сервере отчетов](../../reporting-services/security/configure-basic-authentication-on-the-report-server.md)   
 [Настройка проверки подлинности Windows на сервере отчетов](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md)  
  
  