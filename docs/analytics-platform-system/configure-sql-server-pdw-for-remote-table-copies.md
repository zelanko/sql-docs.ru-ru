---
title: Настройка для удаленной таблицы копии (SQL Server PDW) SQL Server PDW
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 496b4214-5891-404c-8237-c2a1e09db6d5
caps.latest.revision: 11
ms.openlocfilehash: 46fdb88ce3a244946b89f14320229905793564ac
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="configure-sql-server-pdw-for-remote-table-copies"></a>Настройка для удаленной таблицы копии SQL Server PDW
Описывает, как настроить SQL Server PDW для использования функции копирования удаленной таблицы копирование таблиц базы данных SMP SQL Server на серверах, отличных от устройства.  
  
В этом разделе описывается один из шагов конфигурации для настройки копирования удаленной таблицы. Список всех шагов см. в разделе [удаленной копии таблицы](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Перед началом  
Чтобы настроить SQL Server PDW использовать копию удаленной таблицы, необходимо выполнить следующее:  
  
-   Учетной записи администратора система платформы аналитики возможность входить непосредственно в ***appliance_domain *-AD01** и ***appliance_domain *-AD02** узлов.  
  
-   Знаете имя узла или IP-имя конечного сервера.  
  
## <a name="HowToPDW"></a>Настройка SQL Server PDW для копирования удаленной таблицы: обновить имена узла в DNS  
**CREATE REMOTE TABLE** оператор, используемый для копирования удаленной таблицы указывает на целевой сервер с помощью IP-адрес или IP-имя системы SMP Windows. Чтобы использовать IP-имя, необходимо добавить элементы для успешное разрешение имен на DNS-сервер.  
  
Ниже описывается, как обновить DNS-сервера.  
  
1.  Выполните вход на активный узел AD (обычно ***appliance_domain *-AD01**).  
  
2.  Откройте диспетчер DNS. Этот файл находится в разделе **Администрирование** в **запустить** меню.  
  
3.  Используйте диспетчер DNS для добавления IP-имя.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Использовать DNS-сервер пересылки для разрешения имен DNS не является специализированным](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
