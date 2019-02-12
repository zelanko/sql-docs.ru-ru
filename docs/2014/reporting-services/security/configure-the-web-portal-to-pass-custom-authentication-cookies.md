---
title: Настройка диспетчера отчетов для передачи файлов cookie пользовательской проверки подлинности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6787ec73d91b32e0bdb90f8a5f25499f0ac35620
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034495"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>Настройка передачи куки-файлов для нестандартной проверки подлинности пользователя в диспетчере отчетов
  При использовании пользовательского модуля проверки подлинности необходимо настроить диспетчер отчетов для передачи куки-файлов для проверки подлинности пользователя. Иначе диспетчер отчетов будет передавать куки-файлы только через HTTP-запрос для сервера отчетов. Чтобы передать дополнительные куки-файлы, необходимо изменить файл RSReportServer.Config.  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>Изменение файла RSReportServer.Config  
 Чтобы включить передачу диспетчером отчетов дополнительных куки-файлов через сервер отчетов, необходимо добавить элемент <`PassThroughCookies`> к настройкам конфигурации диспетчера отчетов в файле RSReportServer.config. Использование дополнительных куки-файлов удобно в решениях однократной проверки подлинности при входе, когда требуются не только куки-файлы проверки подлинности сервера отчетов, но также куки-файлы от сторонних систем проверки подлинности.  
  
 Чтобы включить передачу дополнительных куки-файлов через HTTP-запрос при использовании диспетчера отчетов, установите следующие элементы в файле RSReportServer.config:  
  
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
  
## <a name="see-also"></a>См. также  
 [Проверка подлинности с использованием сервера отчетов](authentication-with-the-report-server.md)   
 [Файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md)   
 [Общие сведения о модулях безопасности](../extensions/security-extension/security-extensions-overview.md)   
 [Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
