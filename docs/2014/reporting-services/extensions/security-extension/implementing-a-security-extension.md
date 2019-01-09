---
title: Реализация модуля безопасности | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- forms-based authentication [Reporting Services]
- custom authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: d2327e7c-0d48-49e3-bcd9-3bba4e67a68b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ba1efc734b49f62b1f7b3b3876a8ea0db2732da7
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53373356"
---
# <a name="implementing-a-security-extension"></a>Реализация модуля безопасности
  Проверка подлинности [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows является основной системой защиты отчетов в службах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Однако в определенных случаях может понадобиться расширить систему безопасности служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], чтобы обеспечить соответствие требованиям системы безопасности предприятия. Для этого используется платформа разработки, предоставляемая API служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. В этом разделе представлены общие сведения о модулях безопасности в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Полные сведения о реализации, развертывании и удалении модулей безопасности служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] см. на странице [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о модулях безопасности](security-extensions-overview.md)  
 Приводит общие сведения о модулях безопасности служб Reporting Services.  
  
 [Проверка подлинности в службах Reporting Services](authentication-in-reporting-services.md)  
 Обсуждается проверка подлинности в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Авторизация в службах Reporting Services](authorization-in-reporting-services.md)  
 Рассматривает авторизацию в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
