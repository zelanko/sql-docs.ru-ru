---
title: "MSSQLSERVER_7308 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b1566e13224284179f42dc24002e37dec0063e17
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver7308"></a>MSSQLSERVER_7308
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7308|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|RMT_STA_DISABLED|  
|Текст сообщения|Поставщик OLE DB '%ls' не может быть использован для распределенных запросов, так как он настроен для запуска в потоке контейнера с одним потоком.|  
  
## <a name="explanation"></a>Объяснение  
Использован поставщик OLE DB, настроенный для запуска в потоке контейнера с одним потоком (STA). Поставщики OLE DB, которые работают в потоке контейнера с одним потоком (STA), не могут быть использованы для распределенных запросов.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы устранить эту ошибку, настройте поставщик для запуска в потоке контейнера с несколькими потоками (MTA). Если поставщик не поддерживает несколько потоков и не может быть обновлен до версии, совместимой с MTA, рассмотрите возможность настройки поставщика для внепроцессного выполнения. Информацию о том, поддерживает ли поставщик режим MTA и может ли он выполняться внепроцессно, можно получить у соответствующего разработчика.  
  

