---
title: "Настройка передачи куки-файлов для нестандартной проверки подлинности пользователя в диспетчере отчетов | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "проверка подлинности [службы Reporting Services]"
  - "модули [службы Reporting Services], настраиваемая безопасность"
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 18
---
# Настройка передачи куки-файлов для нестандартной проверки подлинности пользователя в диспетчере отчетов
  При использовании пользовательского модуля проверки подлинности необходимо настроить [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] для передачи файлов cookie пользовательской проверки подлинности. В противном случае [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] будет передавать файлы cookie только через HTTP-запрос для сервера отчетов. Чтобы передать дополнительные куки-файлы, необходимо изменить файл RSReportServer.Config.  
  
## Изменение файла RSReportServer.Config  
 Чтобы включить передачу [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] дополнительных файлов cookie через сервер отчетов, необходимо добавить элемент \<**PassThroughCookies**> к настройкам конфигурации [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] в файле RSReportServer.config. Использование дополнительных куки-файлов удобно в решениях однократной проверки подлинности при входе, когда требуются не только куки-файлы проверки подлинности сервера отчетов, но также куки-файлы от сторонних систем проверки подлинности.  
  
 Чтобы включить передачу дополнительных файлов cookie через HTTP-запрос при использовании [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)], установите следующие элементы в файле RSReportServer.config:  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## См. также:  
 [Проверка подлинности с использованием сервера отчетов](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Общие сведения о модулях безопасности](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
 [Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  