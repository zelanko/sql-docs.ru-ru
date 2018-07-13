---
title: MSSQLSERVER_9001 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9731255f02d9238aab220694bd198ec11bbb31b0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413843"
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
  
  
