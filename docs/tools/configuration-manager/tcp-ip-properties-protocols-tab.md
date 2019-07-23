---
title: Свойства TCP/IP (вкладка «Протоколы») | Документация Майкрософт
ms.custom: ''
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
ms.openlocfilehash: ef748c0b53ecd4812816bfc021567e91fbc10c52
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023792"
---
# <a name="tcpip-properties-protocols-tab"></a>Свойства TCP/IP (вкладка «Протоколы»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
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
  
  
