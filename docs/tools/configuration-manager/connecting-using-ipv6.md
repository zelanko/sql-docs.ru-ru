---
title: Соединение с использованием IPv6
description: Узнайте о поддержке протоколов IPv4 и IPv6 в SQL Server и SQL Server Native Client, а также о том, как настроить ядро СУБД для адреса, который вы хотите использовать.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Internet Protocol
- IPv4
- IPv6
ms.assetid: 2669098c-f5f1-43da-aec6-e91003ac89f6
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 698d201e07ef7e84bcc552d9ec815012af2d968d
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88900525"
---
# <a name="connecting-using-ipv6"></a>Соединение с использованием IPv6
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] полностью поддерживают протокол IP версии 4 (IPv4) и версии 6 (IPv6). Если в Windows настроен протокол IPv6, то компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]автоматически обнаруживают наличие IPv6. Дополнительно настраивать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требуется.  
  
 Поддержка включает в себя в том числе следующее.  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и другие серверные компоненты могут прослушивать адреса IPv4 и IPv6 одновременно. При наличии как IPv4, так и IPv6 можно с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроить компоненты [!INCLUDE[ssDE](../../includes/ssde-md.md)] на прослушивание только адресов IPv4 или только адресов IPv6.  
  
-   Если служба « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , браузер» выполняется в системе с поддержкой IPv4 и IPv6 и поступает запрос на адрес IPv4, то в ответ выдается адрес IPv4 и первый TCP-порт IPv4 из списка. При запросе адреса IPv6 возвращается адрес IPv6 и первый TCP-порт IPv6 из списка. Во избежание несогласованности рекомендуется настроить средства прослушивания IPv4 и IPv6 на один и тот же порт.  
  
-   Такие средства, как среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , допускают IP-адреса в форматах IPv4 и IPv6. В большинстве случаев в строку подключения не требуется вносить изменения, если параметры \<*computer_name*>\\<*имя_экземпляра*> заданы с использованием имени узла сервера либо полного доменного имени (FQDN). Если на сервере установлена поддержка IPv4 и IPv6, имя узла либо FQDN разрешается в несколько IP-адресов, в том числе не менее одного адреса IPv4 и нескольких адресов IPv6. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Собственный клиент пытается установить соединения с помощью этих IP-адресов в порядке, заданном TCP/IP, и использует первое успешное соединение. Поскольку порядок попыток соединения не может быть спрогнозирован собственным клиентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , его следует рассматривать как случайный. Если присутствуют адреса IPv4 и IPv6, то первыми проверяются адреса IPv4. Эта логика прозрачна для пользователей ODBC, OLE DB и ADO.NET.  
  
    > [!NOTE]  
    >  Если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не прослушивает протокол IPv4, то соединение по IPv4 должна дождаться истечения тайм-аута перед попыткой соединения по адресу IPv6. Чтобы этого избежать, следует подключаться непосредственно к IP-адресу IPv6 либо задать псевдоним адреса IPv6 на клиенте.  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md)  
  
  
