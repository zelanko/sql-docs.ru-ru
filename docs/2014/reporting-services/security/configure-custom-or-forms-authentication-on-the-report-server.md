---
title: Настройка нестандартной проверки подлинности или проверки подлинности с помощью форм на сервере отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Forms authentication, configuring
- custom authentication [Reporting Services]
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e568d04a58ad13479f0e3a58254f8e409c46164d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56010825"
---
# <a name="configure-custom-or-forms-authentication-on-the-report-server"></a>Настройка нестандартной проверки подлинности или проверку подлинности с помощью форм на сервере отчетов
  Службы Reporting Services предоставляют открытую архитектуру, которая позволяет подключать нестандартные модули проверки подлинности и модули проверки подлинности с помощью форм. Можно рассмотреть возможность реализации нестандартного модуля проверки подлинности, если требования к развертыванию не включают встроенной безопасности Windows или обычную проверку подлинности. Наиболее распространенный сценарий использования нестандартной проверки подлинности — доступ к веб-приложению через Интернет или экстрасеть. Замена модуля проверки подлинности Windows по умолчанию нестандартным модулем проверки подлинности обеспечивает более широкие возможности управления предоставлением доступа к серверу отчетов внешним пользователям.  
  
 На практике для развертывания нестандартного модуля проверки подлинности требуется выполнить несколько шагов, в том числе копировать сборки и файлы приложений, изменять файлы конфигурации и выполнять тестирование. В этом разделе рассматриваются только параметры проверки подлинности, указанные в файлах конфигурации.  
  
> [!NOTE]  
>  Чтобы создать нестандартный модуль проверки подлинности, необходимо написать определенный код и хорошо разбираться в системе безопасности [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Если не нужно создавать нестандартный модуль проверки подлинности, можно использовать группы и учетные записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory, но это связано со значительным уменьшением области развертывания сервера отчетов. Дополнительные сведения о нестандартной проверке подлинности см. в разделе [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md).  
  
 Кроме того, если нужно использовать проверку подлинности с помощью форм или нестандартный модуль проверки подлинности в среде служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , интегрированной с продуктом SharePoint, то необходимо настроить сайт SharePoint на использование выбранного метода проверки подлинности. Дополнительные сведения о настройке проверки подлинности в SharePoint см. в разделе [Authentication Samples](https://go.microsoft.com/fwlink/?LinkId=115575) в библиотеке MSDN [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
### <a name="to-configure-a-report-server-to-use-custom-authentication"></a>Настройка сервера отчетов для использования нестандартной проверки подлинности  
  
1.  Откройте файл конфигурации RSReportServer.config в текстовом редакторе.  
  
2.  Найдите <`Authentication`>.  
  
3.  Скопируйте следующую структуру XML:  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  Вставьте его на место существующих элементов <`Authentication`>.  
  
     Следует заметить, что `Custom` нельзя использовать с другими типами проверки подлинности.  
  
5.  Сохраните файл.  
  
6.  Откройте файл конфигурации Web.config для сервера отчетов. По умолчанию он находится в \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer.  
  
7.  Найдите параметр `authentication mode` и установите значение `Forms`.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  Найдите параметр `identity impersonate` и установите значение `False`.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. Откройте файл конфигурации Web.config для диспетчера отчетов. По умолчанию она находится в каталоге «\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager».  
  
10. Найдите параметр `authentication mode` и установите значение `Forms`.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. Найдите параметр `identity impersonate` и установите значение `False`.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. Добавьте элемент структуры `PassThroughCookies` к файлу конфигурации. Дополнительные сведения см. в разделе [Настройка передачи куки-файлов для нестандартной проверки подлинности пользователя в диспетчере отчетов](configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
13. Сохраните файл.  
  
14. Если настроено масштабное развертывание, повторите все предыдущие шаги для других серверов отчетов в развертывании.  
  
15. Перезапустите сервер отчетов, чтобы очистить все открытые сеансы.  
  
## <a name="see-also"></a>См. также  
 [Implementing a Security Extension](../extensions/security-extension/implementing-a-security-extension.md)   
 [Проверка подлинности с использованием сервера отчетов](authentication-with-the-report-server.md)   
 [Файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md)   
 [Настройка обычной проверки подлинности на сервере отчетов](configure-basic-authentication-on-the-report-server.md)   
 [Настройка проверки подлинности Windows на сервере отчетов](configure-windows-authentication-on-the-report-server.md)  
  
  
