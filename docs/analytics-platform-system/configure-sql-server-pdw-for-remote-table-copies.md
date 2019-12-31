---
title: Копирование удаленных таблиц
description: Описывает настройку параллельного хранилища данных для использования функции копирования удаленных таблиц для копирования таблиц в базы данных SMP SQL Server на серверах, не поддерживающих устройства.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6c9a0a29b543eb287c7e233d6b1ea77bb2a0d45c
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401266"
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>Настройка параллельного хранилища данных для удаленных копий таблиц
Описывает, как настроить SQL Server PDW для использования функции копирования удаленных таблиц для копирования таблиц в базы данных SMP SQL Server на серверах без устройств.  
  
В этом разделе описывается один из шагов настройки для настройки копирования удаленной таблицы. Список всех шагов настройки см. в разделе [Удаленная копия таблицы](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Перед началом работы  
Чтобы настроить SQL Server PDW для использования копирования из удаленной таблицы, необходимо выполнить следующие действия.  
  
-   Иметь учетную запись администратора системы аналитики, с возможностью непосредственного входа в узлы <strong> *appliance_domain*-AD01</strong> и <strong> *appliance_domain*-AD02</strong> .  
  
-   Сведения об имени узла или IP-имени целевого сервера.  
  
## <a name="HowToPDW"></a>Настройка SQL Server PDW для копирования удаленных таблиц: обновление имен узлов в DNS  
Инструкция **CREATE Remote Table** , используемая для копирования удаленных таблиц, указывает целевой сервер, используя IP-адрес или IP-имя системы SMP в системе Windows. Чтобы использовать IP-имя, необходимо добавить записи для успешного разрешения имен на DNS-сервер.  
  
Ниже описаны действия по обновлению DNS-сервера.  
  
1.  Войдите в активный узел AD (обычно <strong> *appliance_domain*-AD01</strong>).  
  
2.  Откройте диспетчер DNS. Он находится в разделе **Администрирование** в меню **Пуск** .  
  
3.  Добавьте имя IP-адреса с помощью диспетчера DNS.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Использование DNS-сервера пересылки для разрешения DNS-имен, отличных от устройств](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
