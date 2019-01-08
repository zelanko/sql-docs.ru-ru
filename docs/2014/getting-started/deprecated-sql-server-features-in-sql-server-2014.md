---
title: Устаревшие функции SQL Server в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4abd066dd2fc971528468fb7104cb0c11e088150
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348789"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Функции SQL Server, устаревшие в SQL Server 2014
  В этом разделе описаны устаревшие функции, которые все еще доступны в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Эти функции будут удалены в следующем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не следует использовать устаревшие функции в новых приложениях.  
  
## <a name="features-not-supported-in-the-next-version-of-includessnoversionincludesssnoversion-mdmd"></a>Функции, неподдерживаемые в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
 Следующие функции компонента [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] не будут поддерживаться в следующей версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Не используйте их при работе над новыми приложениями и как можно скорее измените приложения, в которых они в настоящее время используются. Название компонента отображается в событиях трассировки в столбце ObjectName, а в счетчиках производительности и в динамическом административном представлении sys.dm_os_performance_counters в столбце instance_name. Идентификатор компонента отображается в событиях трассировки в столбце ObjectId.  
  
|Категория|Устаревшая функция|Замена|Имя функции|Идентификатор функции|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Программирование данных|[методы sys.soap_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Технология Windows Communications Foundation (WCF) или ASP.NET|Собственные веб-службы с поддержкой XML|22|  
|Программирование данных|[sys.endpoint_webmethods &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Технология Windows Communications Foundation (WCF) или ASP.NET|Собственные веб-службы с поддержкой XML|23|  
  
### <a name="slipstream-functionality"></a>Функции интегрированной установки  
 Функция обновления продукта является заменой функции интегрированной установки, которая была доступна в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1. Поэтому параметры командной строки /*PCUSource* и /*CUSource*, связанные с функцией интегрированной установки, больше не должны использоваться. Эти параметры будут оставаться применимыми, но могут быть удалены в будущих версиях программы установки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Параметр /*UpdateSource* объединяет функциональность параметров Slipstream, /*PCUSource* и /*CUSource*.  
  
 Дополнительные сведения о функции интегрированной установки, который был доступен в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1, см. в разделе [интегрированная установка обновлений SQL Server](https://go.microsoft.com/fwlink/?LinkId=219945) (https://go.microsoft.com/fwlink/?LinkId=219945).  
  
## <a name="see-also"></a>См. также  
 [Обратная совместимость](../../2014/getting-started/backward-compatibility.md)  
  
  
