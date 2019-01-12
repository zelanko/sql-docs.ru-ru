---
title: Настройка для копий удаленных таблиц Parallel Data Warehouse | Документация Майкрософт
description: В этой статье описывается настройка Parallel Data Warehouse, в которых будет производиться копирование таблиц базы данных SMP SQL Server на серверах не является специализированным функцией копирования удаленной таблицы.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: fdac0b6ed211e223c3fad7ba15ac79a282c61303
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54123919"
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>Настройка Parallel Data Warehouse для копий удаленных таблиц
В этой статье описывается настройка PDW SQL Server, в которых будет производиться копирование таблиц базы данных SMP SQL Server на серверах не является специализированным функцией копирования удаленной таблицы.  
  
В этом разделе описывает один из шагов конфигурации для настройки копирования удаленной таблицы. Список все действия по настройке, см. в разделе [копирование удаленной таблицы](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Перед началом  
Чтобы настроить SQL Server PDW использовать копирование удаленных таблиц, необходимо сделать следующее:  
  
-   Иметь учетную запись администратора системы платформы аналитики с возможность входа непосредственно в  <strong>*appliance_domain*-AD01</strong> и  <strong>*appliance_domain*-AD02</strong> узлов.  
  
-   Знаете имя узла или IP-имя конечного сервера.  
  
## <a name="HowToPDW"></a>Настройка SQL Server PDW для копирования удаленной таблицы: Обновление имен узла в DNS  
**CREATE REMOTE TABLE** оператор, используемый для копий удаленных таблиц, указывает конечный сервер с помощью IP-адрес или IP-имя системы Windows SMP. Чтобы использовать IP-имя, необходимо добавить записи для успешное разрешение имен на DNS-сервер.  
  
Ниже приведены инструкции для обновления DNS-сервера.  
  
1.  Войдите на активный узел AD (обычно  <strong>*appliance_domain*-AD01</strong>).  
  
2.  Откройте диспетчер DNS. Этот файл находится в разделе **Администрирование** в **запустить** меню.  
  
3.  Используйте диспетчер DNS, чтобы добавить IP-имя.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Используйте DNS-сервера пересылки для разрешения имен DNS не является специализированным](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
