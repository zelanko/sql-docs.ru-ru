---
title: "MSSQLSERVER_233 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "233"
helpviewer_keywords:
- 233 (Database Engine error)
ms.assetid: 201665dc-7ac8-4c19-90d3-33354c5caa72
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a029352dec1ac5a700b7ad5d048a9cb630347462
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver233"></a>MSSQLSERVER_233
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|233|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Соединение с сервером было успешно установлено, но при входе в систему произошла ошибка. (Поставщик: поставщик общей памяти, ошибка: 0 — На другом конце канала отсутствует процесс.) (Microsoft SQL Server, ошибка: 233)|  
  
## <a name="explanation"></a>Объяснение  
Клиенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается установить соединение с сервером. Эта ошибка может возникать, если на сервере не настроен прием удаленных соединений.  
  
## <a name="user-action"></a>Действие пользователя  
С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешите в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прием удаленных соединений.  
  
## <a name="see-also"></a>См. также:  
[Сетевые протоколы и библиотеки](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Включение или отключение сетевого протокола сервера](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  

