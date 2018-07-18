---
title: Настройка параллельного хранилища данных для удаленной таблицы копий | Документы Microsoft
description: В этой статье описывается настройка параллельного хранилища данных для использования функции копирования удаленной таблицы копирование таблиц базы данных SMP SQL Server на серверах, отличных от устройства.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3f71a0c67639918820bca8f6f8f38b9f354154f3
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539534"
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>Настройка для удаленной таблицы копии Parallel Data Warehouse
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
  
