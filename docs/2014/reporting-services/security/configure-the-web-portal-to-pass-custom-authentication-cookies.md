---
title: Настройка диспетчер отчетов для передачи файлов cookie пользовательской проверки подлинности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34f637ee2d0a8235f21167df78178c4de9292c8c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66102045"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>Настройка передачи куки-файлов для нестандартной проверки подлинности пользователя в диспетчере отчетов
  При использовании пользовательского модуля проверки подлинности необходимо настроить диспетчер отчетов для передачи куки-файлов для проверки подлинности пользователя. Иначе диспетчер отчетов будет передавать куки-файлы только через HTTP-запрос для сервера отчетов. Чтобы передать дополнительные куки-файлы, необходимо изменить файл RSReportServer.Config.  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>Изменение файла RSReportServer.Config  
 Можно включить диспетчер отчетов для передачи дополнительных файлов cookie на сервер отчетов, добавив <`PassThroughCookies` элемент> в параметры конфигурации диспетчер отчетов в файле RSReportServer. config. Использование дополнительных куки-файлов удобно в решениях однократной проверки подлинности при входе, когда требуются не только куки-файлы проверки подлинности сервера отчетов, но также куки-файлы от сторонних систем проверки подлинности.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Проверка подлинности с использованием сервера отчетов](authentication-with-the-report-server.md)   
 [Файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md)   
 [Общие сведения о модулях безопасности](../extensions/security-extension/security-extensions-overview.md)   
 [Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
