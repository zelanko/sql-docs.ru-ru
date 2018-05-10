---
title: MSSQLSERVER_17130 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e715843dd8a6bca9a8fad8f5dc6b3b62eef0ae5c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17130"></a>MSSQLSERVER_17130
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17130|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|INIT_NOLOCKSPACE|  
|Текст сообщения|Недостаточно памяти для заданного количества блокировок. Выполняется попытка запуска с хэш-таблицей блокировок меньшего размера, что может негативно отразиться на производительности. Обратитесь к администратору базы данных с просьбой о выделении большего объема памяти для данного экземпляра компонента Database Engine.|  
  
## <a name="explanation"></a>Объяснение  
Недостаточно памяти для хэш-таблицы диспетчера блокировок нужного размера.  Будет произведена попытка запуска с уменьшенным размером хэш-таблицы блокировок.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте параметры конфигурации памяти сервера (min/max server memory) и нагрузку на память. Предоставьте больше памяти для работы SQL Server.  
  
