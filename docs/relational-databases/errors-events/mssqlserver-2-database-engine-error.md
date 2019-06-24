---
title: MSSQLSERVER_2 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3b53ff4ae1449cf0aba42ba61aa3e864d38fb15e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028865"
---
# <a name="mssqlserver2"></a>MSSQLSERVER_2
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|При соединении с сервером произошла ошибка.  Эта ошибка при соединении с SQL Server может быть вызвана тем, что в параметрах SQL Server по умолчанию запрещены удаленные соединения. (поставщик: поставщик именованных каналов, ошибка: 40: не удалось открыть соединение с SQL Server (поставщик данных .Net SqlClient)|  
  
## <a name="explanation"></a>Объяснение  
Вероятно, от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поступил ответ на запрос клиента, потому что этот сервер не был запущен.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что сервер запущен.  
  
## <a name="see-also"></a>См. также:  
[Управление службами ядра СУБД](~/database-engine/configure-windows/manage-the-database-engine-services.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Сетевые протоколы и библиотеки](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Включение или отключение сетевого протокола сервера](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
