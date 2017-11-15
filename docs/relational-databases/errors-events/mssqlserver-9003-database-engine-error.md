---
title: "MSSQLSERVER_9003 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 7a383a9f0ac779c37d4fe9cb56dd2233ccc59215
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver9003"></a>MSSQLSERVER_9003
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9003|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LOG_INVALID_LSN|  
|Текст сообщения|Передан недопустимый номер %S_LSN для просмотра журнала в базе данных «%.*ls». Эта ошибка может свидетельствовать о повреждении данных или о том, что файл журнала (LDF) не соответствует файлу данных (MDF). Если она возникла во время репликации, повторно создайте публикацию. В противном случае, если ошибка приводит к сбою при загрузке, произведите восстановление из резервной копии.|  
  
## <a name="explanation"></a>Объяснение  
Компонент передал менеджеру журнала базы данных недопустимый регистрационный номер транзакции в журнале. Это может быть вызвано проблемами репликации, повреждением данных или несоответствием между первичным файлом данных и файлом журнала.  
  
## <a name="user-action"></a>Действие пользователя  
Если эта ошибка возникла во время репликации, повторно создайте публикацию. В противном случае выполните восстановление из резервной копии.  
  
