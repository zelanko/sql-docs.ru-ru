---
title: MSSQLSERVER_17130 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4f8d62a98d39a65db78f79fdfaf3ecdb2921408e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915376"
---
# <a name="mssqlserver_17130"></a>MSSQLSERVER_17130
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17130|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|INIT_NOLOCKSPACE|  
|Текст сообщения|Недостаточно памяти для заданного количества блокировок. Выполняется попытка запуска с хэш-таблицей блокировок меньшего размера, что может негативно отразиться на производительности. Обратитесь к администратору базы данных с просьбой о выделении большего объема памяти для данного экземпляра компонента Database Engine.|  
  
## <a name="explanation"></a>Объяснение  
 Недостаточно памяти для хэш-таблицы диспетчера блокировок нужного размера.  Будет произведена попытка запуска с уменьшенным размером хэш-таблицы блокировок.  
  
## <a name="user-action"></a>Действие пользователя  
 Проверьте параметры конфигурации памяти сервера (min/max server memory) и нагрузку на память. Предоставьте больше памяти для работы SQL Server.  
  
  
