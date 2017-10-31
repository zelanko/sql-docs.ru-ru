---
title: "MSSQLSERVER_9001 | Документация Майкрософт"
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
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1eaae857105a13a133c2fc9cd216d701df9f51d5
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver9001"></a>MSSQLSERVER_9001
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9001|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LOG_NOT_AVAIL|  
|Текст сообщения|Журнал для базы данных «%.*ls» недоступен. Проверьте журнал событий на наличие сообщений о связанных ошибках. Устраните все ошибки и заново запустите базу данных.|  
  
## <a name="explanation"></a>Объяснение  
Журнал базы данных переведен в режим «вне сети». Обычно это означает серьезный сбой и необходимость перезапуска базы данных.  
  
## <a name="user-action"></a>Действие пользователя  
Найдите остальные ошибки и перезапустите экземпляр SQL Server, если он еще не перезапустился самостоятельно.  
  

