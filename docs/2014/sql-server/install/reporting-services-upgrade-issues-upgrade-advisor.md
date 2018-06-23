---
title: Обновление служб Reporting Services проблемы (Советник по переходу) | Документы Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 68e688e416c0d4a001492f9372e8363f558f8a26
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191553"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Проблемы обновления служб Reporting Services (помощник по обновлению)
  В следующих разделах описываются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] проблемы, которые могут возникнуть при обновлении до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В следующих разделах описаны действия, позволяющие смягчить воздействие этих изменений на рабочую среду.  
  
 Помощник по обновлению анализирует установленный экземпляр сервера отчетов. Если установлены только клиентские компоненты (например, единственным установленным на компьютер компонентом служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] является конструктор отчетов), никаких сообщений о проблемах не появится.  
  
 В зависимости от конфигурации установленного экземпляра могут встретиться дополнительные проблемы, о которых помощник по обновлению не сообщает. Эти проблемы не помешают успешному обновлению служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], но могут повлиять на работу отчетов и приложений после завершения обновления. Дополнительные сведения о таких проблемах см. в разделе «Обратная совместимость служб Reporting Services» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если невозможно использовать программу установки для обновления имеющегося экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], можно установить новый экземпляр служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и перенести на него существующий экземпляр. Дополнительные сведения см. в разделе «Обновление и перенос служб Reporting Services» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации [обновление и перенос служб Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 В следующих разделах описываются известные проблемы, о которых может сообщать помощник по обновлению, и объясняется, как изменить существующий экземпляр, чтобы обеспечить возможность обновления.  
  
> [!IMPORTANT]  
>  Чтобы выполнить анализ экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], необходимо установить советник по переходу на сервере отчетов. Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не поддерживают удаленный анализ.  
>   
>  Дополнительные сведения см. в разделе [установка помощника по обновлению](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Сертификаты клиента на веб-сайт сервера отчетов &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [На сервере отчетов обнаружены пользовательские расширения &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [На сервере отчетов обнаружены пользовательские элементы отчета &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Не найдены компоненты обратной совместимости служб IIS &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [Обнаружено ограничение IP-адреса &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [На сайте сервера отчетов обнаружены фильтры ISAPI &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [На компьютере сервера отчетов обнаружены устаревшие модули &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [База данных сервера отчетов не настроен &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [Обнаружена группа веб-служб сервера отчетов SQL Server 2005 &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [Виртуальные каталоги не указаны &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [Виртуальный каталог использует неподдерживаемый метод проверки подлинности &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [Изменения ограничений ЦП и памяти для SQL Server Standard и Enterprise &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [Для фермы SharePoint требуются учетные записи домена &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [Прямой переход на сервер отчетов &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Установлен Microsoft SharePoint 2007 &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [Microsoft SQL Server SharePoint общей службы Reporting Services будет установлена параллельно &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [Параметры сортировки сервера несовместимые базы данных ядра &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [Проблемы обновления служб создания отчетов](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  