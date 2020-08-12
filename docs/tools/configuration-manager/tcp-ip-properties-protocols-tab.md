---
title: Свойства TCP/IP (вкладка «Протоколы»)
description: Используйте параметры на вкладке "Протоколы" диалогового окна свойств TCP/IP для настройки интервала проверки активности, флага включения и других свойств.
ms.custom: seo-lt-2019
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2e9bf22b501a097e59af3bef953ffcbaa26780c1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85880289"
---
# <a name="tcpip-properties-protocols-tab"></a>Свойства TCP/IP (вкладка «Протоколы»)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Используйте диалоговое окно **Свойства TCP/IP** для настройки параметров протокола TCP/IP. Щелкните пункт **TCP/IP** в левой панели, чтобы вывести настройки отдельных IP-адресов в панель сведений.  
  
 Чтобы изменения вступили в силу, необходимо перезапустить Microsoft SQL Server.  
  
## <a name="options"></a>Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**.  
  
 **Keep Alive**  
 Задайте интервал (в миллисекундах), через который будут отправляться пакеты проверки активности для проверки доступности компьютера на удаленном конце соединения.  
  
 **Listen All**  
 Укажите, должен ли SQL Server прослушивать все IP-адреса, привязанные к сетевым адаптерам компьютера. Если параметр имеет значение **Нет**, настройте каждый IP-адрес отдельно при помощи диалогового окна свойств для каждого IP-адреса. Если параметр имеет значение **Да**, то настройки, находящиеся в диалоговом окне свойств **IPAll** , будут применяться ко всем IP-адресам. Значение по умолчанию — **Да**.  
  
 **No Delay**  
 SQL Server не реализует изменения этого свойства.  
  
## <a name="see-also"></a>См. также:  
 [Выбор сетевого протокола](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [Создание допустимой строки подключения с использованием протокола TCP/IP](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
