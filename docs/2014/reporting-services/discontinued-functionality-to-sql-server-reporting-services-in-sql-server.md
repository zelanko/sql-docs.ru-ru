---
title: Неподдерживаемые функции
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 8cdec8ed3fbdd539b0c630af2a298ebf9807d6a7
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755753"
---
# <a name="discontinued-functionality-in-sql-server-reporting-services-ssrs"></a>Неподдерживаемая функциональность в службах SQL Server Reporting Services (SSRS)

  В этой статье описаны функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , которые больше недоступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Сюда не входят объявления о прекращении поддержки определенных версий операционных систем или служб [!INCLUDE[msCoName](../includes/msconame-md.md)] IIS. Дополнительные сведения о системных требованиях см. в разделе [требования к оборудованию и программному обеспечению для установки SQL Server 2014](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
 В этом разделе:  
  
- [SQL Server 2014 Reporting Services неподдерживаемые функции](#bkmk_sql14)  
  
- [Неподдерживаемые возможности в службах SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
- [Неподдерживаемые возможности в службах SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-discontinued-functionality"></a><a name="bkmk_sql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Reporting Services неподдерживаемые функции

 В [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отсутствуют неподдерживаемые функции служб [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="sssql11-reporting-services-discontinued-functionality"></a><a name="bkmk_rc0"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]Reporting Services неподдерживаемые функции

 В этом разделе описаны неподдерживаемые функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
 В [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отсутствуют неподдерживаемые функции служб [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="sql-server-2008-r2-reporting-services-discontinued-functionality"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services неподдерживаемые функции

 В этом разделе описывается прекращение работы в [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
> [!NOTE]  
> Поскольку SQL Server 2008 R2 содержит изменения дополнительного номера версии по сравнению с SQL Server 2008, рекомендуется также просмотреть содержимое раздела по SQL Server 2008.
  
### <a name="64-bit-platform-support"></a>Поддержка 64-разрядной платформы

 Начиная с выпуска [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] компонент служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживает серверы на основе процессоров Itanium под управлением Windows Server 2003 или Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] по-прежнему поддерживает другие 64-разрядные ОС, в том числе Windows Server 2008 и Windows Server 2008 R2 для систем на основе процессоров Itanium. Чтобы обновить установленный экземпляр [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] со службами [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], работающий под управлением Windows Server 2003 или Windows Server 2003 R2 для систем на основе процессоров Itanium, до выпуска [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], необходимо предварительно обновить операционную систему.  
  
### <a name="data-source-credentials-in-url-access"></a>Учетные данные источника данных при доступе через URL-адрес

 Строки параметров доступа по URL-адресу *DSU: Источник = значение* и *DSP: Источник = значение* теперь больше не поддерживаются. В предыдущих версиях эти строки параметров хранились в виде открытого текста в кэше браузера, что небезопасно.  
  
## <a name="next-steps"></a>Дальнейшие действия

 - [Новые возможности &#40;Reporting Services&#41;](what-s-new-reporting-services.md)
 - [Изменения в работе служб SQL Server Reporting Services в выпуске SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)
 - [Устаревшие функции служб SQL Server Reporting Services в SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)