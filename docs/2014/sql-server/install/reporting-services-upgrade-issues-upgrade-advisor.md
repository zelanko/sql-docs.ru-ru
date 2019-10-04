---
title: Проблемы обновления Reporting Services (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 75c3bda5d15e3930fcdeba9ca73d70128fd90336
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952060"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Проблемы обновления служб Reporting Services (помощник по обновлению)
  В следующих разделах описываются проблемы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], которые могут повлиять на обновление до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В следующих разделах описаны действия, позволяющие смягчить воздействие этих изменений на рабочую среду.  
  
 Помощник по обновлению анализирует установленный экземпляр сервера отчетов. Если установлены только клиентские компоненты (например, единственным установленным на компьютер компонентом служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] является конструктор отчетов), никаких сообщений о проблемах не появится.  
  
 В зависимости от конфигурации установленного экземпляра могут встретиться дополнительные проблемы, о которых помощник по обновлению не сообщает. Эти проблемы не помешают успешному обновлению служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], но могут повлиять на работу отчетов и приложений после завершения обновления. Дополнительные сведения о таких проблемах см. в разделе «Обратная совместимость служб Reporting Services» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если невозможно использовать программу установки для обновления имеющегося экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], можно установить новый экземпляр служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и перенести на него существующий экземпляр. Дополнительные сведения см. в разделе "обновление и миграция Reporting Services" в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [обновление и миграция Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 В следующих разделах описываются известные проблемы, о которых может сообщать помощник по обновлению, и объясняется, как изменить существующий экземпляр, чтобы обеспечить возможность обновления.  
  
> [!IMPORTANT]  
>  Чтобы выполнить анализ экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], необходимо установить советник по переходу на сервере отчетов. Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не поддерживают удаленный анализ.  
>   
>  Дополнительные сведения см. в разделе [Установка помощника по обновлению](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Клиентские сертификаты на веб-сайте &#40;сервера отчетов советник по переходу&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [В помощнике по обновлению сервера &#40;отчетов обнаружены пользовательские расширения&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [В помощнике по обновлению сервера &#40;отчетов обнаружены пользовательские элементы отчета&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Компоненты обратной совместимости IIS не были &#40;обнаружены советником по переходу&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [Ограничение IP-адресов &#40;обнаружило советник по переходу&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [В помощнике по обновлению сайта &#40;сервера отчетов обнаружены фильтры ISAPI&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [На помощнике по обновлению компьютера &#40;сервера отчетов обнаружены устаревшие расширения&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [В базе данных сервера отчетов не &#40;настроен помощник по обновлению&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [SQL Server 2005 группа веб-служб сервера отчетов &#40;обнаружила советник по переходу&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [В виртуальных каталогах не &#40;указан помощник по обновлению&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [В виртуальном каталоге не поддерживается помощник по &#40;обновлению метода проверки подлинности&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [Изменения в ограничениях ресурсов ЦП и памяти для SQL Server Standard &#40;и советника по обновлению предприятия&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [Учетные записи домена, необходимые &#40;для советника по переходу на ферму SharePoint&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [Прямой просмотр помощника по &#40;обновлению сервера отчетов&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Microsoft SharePoint 2007 установлен &#40;советник по переходу&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [Microsoft SQL Server Reporting Services общая служба SharePoint установлена параллельно с советником по &#40;переходу&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [Советник по &#40;переходу ядро СУБД сервера несовместим&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [Другие проблемы обновления служб Reporting Services](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
