---
title: MSSQLSERVER_7308 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3b64f55f2ce7f71a358cc202a428191d5f1998f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209524"
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
  
  
