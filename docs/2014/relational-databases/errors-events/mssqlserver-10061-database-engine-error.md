---
title: MSSQLSERVER_10061 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b77e1d920f97891d173bfdcdcb23ceb6c0acf0c4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870712"
---
# <a name="mssqlserver10061"></a>MSSQLSERVER_10061
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10061|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|При соединении с сервером произошла ошибка.  Эта ошибка при соединении с SQL Server может быть вызвана тем, что в параметрах SQL Server по умолчанию запрещены удаленные соединения. (поставщик: Поставщик TCP, ошибка: 0 — Подключение не установлено, т.к. конечный компьютер отверг запрос на подключение.) (Microsoft SQL Server, ошибка: 10061)|  
  
## <a name="explanation"></a>Объяснение  
 Сервер не ответил на запрос клиента. Возможно, это связано с тем, что сервер не запущен.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что сервер запущен.  
  
## <a name="see-also"></a>См. также  
 [Управление службами компонента Database Engine](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Сетевые протоколы и библиотеки](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Конфигурация клиентской сети](../../database-engine/configure-windows/client-network-configuration.md)   
 [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
