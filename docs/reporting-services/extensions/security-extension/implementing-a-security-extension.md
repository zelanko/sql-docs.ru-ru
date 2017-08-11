---
title: "Реализация модуля безопасности | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- security [Reporting Services], extensions
- forms-based authentication [Reporting Services]
- custom authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: d2327e7c-0d48-49e3-bcd9-3bba4e67a68b
caps.latest.revision: 40
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 51bcbe7ead960439caa55785f50075f8dfdcf3f8
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-a-security-extension"></a>Реализация модуля безопасности
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]Проверка подлинности Windows является основной системой защиты отчетов в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Однако в определенных случаях может понадобиться расширить систему безопасности служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], чтобы обеспечить соответствие требованиям системы безопасности предприятия. Для этого используется платформа разработки, предоставляемая API служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. В этом разделе представлены общие сведения о модулях безопасности в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Подробные сведения о реализации, развертывании и удалении [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модуль безопасности, см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Общие сведения о модулях безопасности](../../../reporting-services/extensions/security-extension/security-extensions-overview.md)  
 Приводит общие сведения о модулях безопасности служб Reporting Services.  
  
 [Проверка подлинности в службах Reporting Services](../../../reporting-services/extensions/security-extension/authentication-in-reporting-services.md)  
 Обсуждается проверка подлинности в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Авторизация в службах Reporting Services](../../../reporting-services/extensions/security-extension/authorization-in-reporting-services.md)  
 Рассматривает авторизацию в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
