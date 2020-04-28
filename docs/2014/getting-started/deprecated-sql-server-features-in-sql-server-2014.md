---
title: Устаревшие функции SQL Server в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44fbab98aa017be66cd4dc369a713f44e8d248d5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75228219"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Функции SQL Server, устаревшие в SQL Server 2014
  В этом разделе описаны устаревшие функции, которые все еще доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Эти функции будут удалены в следующем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
## <a name="features-not-supported-in-the-next-version-of-ssnoversion"></a>Функции, неподдерживаемые в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
 Следующие функции компонента [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] не будут поддерживаться в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не используйте их при работе над новыми приложениями и как можно скорее измените приложения, в которых они в настоящее время используются. Название компонента отображается в событиях трассировки в столбце ObjectName, а в счетчиках производительности и в динамическом административном представлении sys.dm_os_performance_counters в столбце instance_name. Идентификатор компонента отображается в событиях трассировки в столбце ObjectId.  
  
|Категория|Устаревшая функция|Замена|Имя функции|Идентификатор функции|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Программирование данных|[sys. soap_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Технология Windows Communications Foundation (WCF) или ASP.NET|Собственные веб-службы с поддержкой XML|22|  
|Программирование данных|[sys. endpoint_webmethods &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Технология Windows Communications Foundation (WCF) или ASP.NET|Собственные веб-службы с поддержкой XML|23|  
  
### <a name="slipstream-functionality"></a>Функции интегрированной установки  
 [Функция обновления продукта](/previous-versions/sql/sql-server-2012/hh231670(v=sql.110)?redirectedfrom=MSDN) появилась в SQL Server 2012 в качестве расширения для функций интегрированной интеграции, которые были доступны в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1. В SQL Server 2014 для интеграции SQL Server рекомендуется использовать функцию обновления продукта. Поэтому параметры командной строки,/*PCUSource* и/*CUSource*, связанные с исходными функциями интегрированного использования, больше не должны использоваться. Эти параметры будут продолжать работать, но могут быть удалены в будущих выпусках [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] программы установки. Рекомендуемый параметр для использования —/*UpdateSource* , который сочетает в себе функциональные возможности исходных параметров, а также*PCUSource* и/*CUSource*.  
  
 Дополнительные сведения об интегрированных функциях, доступных в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1, см. в разделе об объединении [SQL Server Update](https://go.microsoft.com/fwlink/?LinkId=219945) (https://go.microsoft.com/fwlink/?LinkId=219945).  
 Сведения о том, как использовать или*UpdateSource* для интеграции сборок SQL Server, см. в следующих источниках:
 
 - [Как установить исправление SQL Server 2012 с обновленным пакетом установки (с помощью UpdateSource для получения интеллектуальной установки)](https://blogs.msdn.microsoft.com/jason_howell/2012/08/28/how-to-patch-sql-server-2012-setup-with-an-updated-setup-package-using-updatesource-to-get-a-smart-setup/)
 
 - [SQL Server 2012 программа установки стала более интеллектуальной...](https://techcommunity.microsoft.com/t5/SQL-Server-Support/SQL-Server-2012-Setup-just-got-smarter-8230/ba-p/317440)
 
## <a name="see-also"></a>См. также:  
 [Обратная совместимость](../../2014/getting-started/backward-compatibility.md)  
  
  
