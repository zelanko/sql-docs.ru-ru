---
title: TCP - свойства IP-адреса (вкладка «протоколы») | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b545fbe28e28739b5f66a7beca1ab7c0450ae08a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150457"
---
# <a name="tcp---ip-properties-protocols-tab"></a>TCP - свойства IP-адреса (вкладка «протоколы»)
  Используйте диалоговое окно **Свойства TCP/IP** для настройки параметров протокола TCP/IP. Щелкните пункт **TCP/IP** в левой панели, чтобы вывести настройки отдельных IP-адресов в панель сведений.  
  
 Чтобы изменения вступили в силу, необходимо перезапустить Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**.  
  
 **Keep Alive**  
 Задайте интервал (в миллисекундах), через который будут отправляться пакеты проверки активности для проверки доступности компьютера на удаленном конце соединения.  
  
 **Listen All**  
 Укажите, должен ли SQL Server прослушивать все IP-адреса, привязанные к сетевым адаптерам компьютера. Если параметр имеет значение **Нет**, настройте каждый IP-адрес отдельно при помощи диалогового окна свойств для каждого IP-адреса. Если параметр имеет значение **Да**, то настройки, находящиеся в диалоговом окне свойств **IPAll** , будут применяться ко всем IP-адресам. Значение по умолчанию — **Да**.  
  
 **No Delay**  
 Сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не реализует изменения этого свойства.  
  
## <a name="see-also"></a>См. также  
 [Выбор сетевого протокола](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Создание допустимой строки подключения с использованием протокола TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
