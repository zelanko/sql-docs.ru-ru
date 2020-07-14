---
title: MSSQLSERVER_10061 | Документация Майкрософт
description: Сервер не ответил на запрос клиента в SQL Server. См. объяснение ошибки и возможные способы ее устранения.
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cc775781dfce666ef663b2b3d36b4633524b30e5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781549"
---
# <a name="mssqlserver_10061"></a>MSSQLSERVER_10061
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10061|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|При соединении с сервером произошла ошибка.  Эта ошибка при соединении с SQL Server может быть вызвана тем, что в параметрах SQL Server по умолчанию запрещены удаленные соединения. (поставщик: поставщик TCP, ошибка: 0 — Подключение не установлено, т.к. конечный компьютер отверг запрос на подключение.) (Microsoft SQL Server, ошибка: 10061)|  
  
## <a name="explanation"></a>Объяснение  
Сервер не ответил на запрос клиента. Возможно, это связано с тем, что сервер не запущен.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что сервер запущен.  
  
## <a name="see-also"></a>См. также:  
[Управление службами компонента Database Engine](~/database-engine/configure-windows/manage-the-database-engine-services.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Сетевые протоколы и библиотеки](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Включение или отключение сетевого протокола сервера](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
