---
title: "Свойства TCP/IP (вкладка «протоколы») | Документы Microsoft"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: a37c630af512d85e22b3547eb520aebe22546040
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# Свойства TCP/IP (вкладка «Протоколы»)
  Используйте диалоговое окно **Свойства TCP/IP** для настройки параметров протокола TCP/IP. Щелкните пункт **TCP/IP** в левой панели, чтобы вывести настройки отдельных IP-адресов в панель сведений.  
  
 Чтобы изменения вступили в силу, необходимо перезапустить Microsoft SQL Server.  
  
## Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**.  
  
 **Keep Alive**  
 Задайте интервал (в миллисекундах), через который будут отправляться пакеты проверки активности для проверки доступности компьютера на удаленном конце соединения.  
  
 **Listen All**  
 Укажите, должен ли SQL Server прослушивать все IP-адреса, привязанные к сетевым адаптерам компьютера. Если параметр имеет значение **Нет**, настройте каждый IP-адрес отдельно при помощи диалогового окна свойств для каждого IP-адреса. Если параметр имеет значение **Да**, то настройки, находящиеся в диалоговом окне свойств **IPAll** , будут применяться ко всем IP-адресам. Значение по умолчанию — **Да**.  
  
 **No Delay**  
 SQL Server не реализует изменения этого свойства.  
  
## См. также:  
 [Выбор сетевого протокола](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [Создание допустимой строки подключения с использованием протокола TCP/IP](/sql-docs/docs/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip)  
  
  

