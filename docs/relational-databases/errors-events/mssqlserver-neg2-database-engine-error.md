---
title: MSSQLSERVER_-2 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "-2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 09a5cbc03debdb4fc87986111fb0ac69138715bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67903766"
---
# <a name="mssqlserver-2"></a>MSSQLSERVER_-2
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|-2|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Время ожидания истекло.  Время ожидания истекло до завершения операции, либо сервер не отвечает. (Microsoft SQL Server, ошибка: –2)|  
  
## <a name="explanation"></a>Объяснение  
Клиенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается установить соединение с сервером. Эта ошибка возникает, если брандмауэр сервера отказывает в соединении.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что в брандмауэре на экземпляре сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешен прием соединений.  
  
## <a name="see-also"></a>См. также:  
[Настройка брандмауэра Windows для разрешения доступа к SQL Server](~/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
[Настройка брандмауэра Windows для доступа к компоненту Database Engine](~/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Сетевые протоколы и библиотеки](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Включение или отключение сетевого протокола сервера](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
