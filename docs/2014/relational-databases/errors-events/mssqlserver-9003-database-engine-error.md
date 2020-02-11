---
title: MSSQLSERVER_9003 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c3d994f2166ae468a731203211eeb7a784118e65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62912466"
---
# <a name="mssqlserver_9003"></a>MSSQLSERVER_9003
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9003|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LOG_INVALID_LSN|  
|Текст сообщения|Передан недопустимый номер %S_LSN для просмотра журнала в базе данных «%.*ls». Эта ошибка может свидетельствовать о повреждении данных или о том, что файл журнала (LDF) не соответствует файлу данных (MDF). Если она возникла во время репликации, повторно создайте публикацию. В противном случае, если ошибка приводит к сбою при загрузке, произведите восстановление из резервной копии.|  
  
## <a name="explanation"></a>Объяснение  
 Компонент передал менеджеру журнала базы данных недопустимый регистрационный номер транзакции в журнале. Это может быть вызвано проблемами репликации, повреждением данных или несоответствием между первичным файлом данных и файлом журнала.  
  
## <a name="user-action"></a>Действие пользователя  
 Если эта ошибка возникла во время репликации, повторно создайте публикацию. В противном случае выполните восстановление из резервной копии.  
  
  
