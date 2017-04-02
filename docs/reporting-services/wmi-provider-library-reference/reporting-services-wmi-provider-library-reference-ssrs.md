---
title: "Справочник по библиотеке поставщика WMI служб Reporting Services (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "Reporting Services WMI Provider Library"
apilocation: 
  - "reportingservices.mof"
helpviewer_keywords: 
  - "поставщик WMI [службы Reporting Services], библиотека"
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# Справочник по библиотеке поставщика WMI служб Reporting Services (SSRS)
  Поставщик WMI служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживает операции WMI, позволяющие создавать скрипты и код для изменения параметров сервера и диспетчера отчетов.  
  
 Например, чтобы изменить режим использования встроенной безопасности при соединении сервера отчетов с его базой данных, создайте экземпляр класса MSReportServer_ConfigurationSetting и воспользуйтесь свойством DatabaseIntegratedSecurity экземпляра сервера отчетов. Классы, показанные в следующей таблице, представляют компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Классы определены в пространстве имен [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] или [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] . Все они поддерживают операции считывания и записи. Операции создания не поддерживаются.  
  
## Классы  
 [Класс MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-class.md)  
 Основные сведения, необходимые клиенту для подключения к установленному серверу отчетов.  
  
 [Класс MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
 Представляет установочные параметры и параметры времени выполнения для экземпляра сервера отчетов. Эти параметры хранятся в файле конфигурации для сервера отчетов.  
  
 Дополнительные сведения об операциях WMI см. в документации по пакету SDK WMI, который поставляется вместе с пакетом SDK для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
## См. также  
 [Доступ к поставщику WMI для служб Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [Технический справочник (службы SSRS)](../../reporting-services/technical-reference-ssrs.md)  
  
  