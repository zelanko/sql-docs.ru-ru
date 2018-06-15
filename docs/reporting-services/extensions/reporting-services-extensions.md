---
title: Модули служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
caps.latest.revision: 45
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 8b5005c8bbd1b64b31696804e70a1f1556fa9ba1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33015391"
---
# <a name="reporting-services-extensions"></a>модули служб Reporting Services
  Модульная архитектура служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] обеспечивает возможность расширения. Доступен API управляемого кода, что позволяет легко разрабатывать, устанавливать модули, используемые многими компонентами служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], а также управлять этими модулями. Можно создавать закрытые и общие сборки с помощью платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и добавлять в службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] новые функции, чтобы соответствовать растущим требованиям.  
  
 Уникальная расширяемая архитектура служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] позволяет разработчикам расширять отдельные функции продукта и его компонентов. В настоящее время поддерживается множество модулей, расширяющих возможности обработки данных в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. API обработки данных поддерживает знакомые конструкции и соглашения поставщиков данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], что позволяет разработчикам встраивать в службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] дополнительные возможности обработки данных. Эти модули обработки данных расширяют функциональные возможности сервера отчетов и конструктора отчетов, обеспечивая безукоризненную интеграцию пользовательских данных в отчеты.  
  
 Еще одним поддерживаемым модулем является модуль доставки. API доставки полностью интегрирован с архитектурой [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], что позволяет применять при отправке пользователям уведомлений об отчетах самые разнообразные механизмы доставки. Можно расширить возможности сервера отчетов, чтобы он предоставлял пользователям нестандартные модули доставки, а страницы управления подписками в диспетчере отчетов дополнить так, чтобы они включили поддержку подписок с нестандартными модулями доставки.  
  
 Еще один модуль сервера отчетов, модуль настройки определений отчетов (RDCE), позволяет динамически настроить определение отчета до передачи его механизму обработки. Отчеты могут настраиваться с учетом таких факторов, как пользователи или языки. Например, можно реализовать различные представления для разных пользователей (допустим, руководителей или сотрудников отдела) или настроить отчет на использование разных вариантов макета при подготовке отчета к просмотру, допустим, на французском или арабском языке.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Рекомендации по обеспечению безопасности для модулей](../../reporting-services/extensions/security-considerations-for-extensions.md)  
 Описывает проблемы защиты, связанные с разработкой и развертыванием расширений [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Реализация модуля обработки данных](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)  
 Описывает требования и шаги по реализации модуля обработки данных для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Реализация модуля доставки](../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)  
 Описывает требования и шаги по реализации модуля доставки для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Реализация модуля подготовки отчетов](../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)  
 Содержит введение в разработку модулей подготовки отчетов.  
  
 [Реализация модуля безопасности](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)  
 Описывает требования и шаги по реализации модуля безопасности для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Библиотека модулей Reporting Services](../../reporting-services/extensions/reporting-services-extension-library.md)  
 Содержит справочник по программированию библиотеки API модулей для средств расширения компонента [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
  
