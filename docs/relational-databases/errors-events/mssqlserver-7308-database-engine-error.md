---
title: MSSQLSERVER_7308 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 96a456d18ef0e776970baed251ededac7bf3b2d4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951578"
---
# <a name="mssqlserver7308"></a>MSSQLSERVER_7308
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
