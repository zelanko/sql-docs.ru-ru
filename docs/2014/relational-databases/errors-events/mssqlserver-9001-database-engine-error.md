---
title: MSSQLSERVER_9001 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1a2f311ddd5ae1c6eee51ac3960b36fe1f2716e
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86550799"
---
# <a name="mssqlserver_9001"></a>MSSQLSERVER_9001
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9001|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LOG_NOT_AVAIL|  
|Текст сообщения|Журнал для базы данных «%.*ls» недоступен. Проверьте журнал событий на наличие сообщений о связанных ошибках. Устраните все ошибки и заново запустите базу данных.|  
  
## <a name="explanation"></a>Объяснение  
 Журнал базы данных переведен в режим «вне сети». Обычно это означает серьезный сбой и необходимость перезапуска базы данных.  
  
## <a name="user-action"></a>Действие пользователя  
 Найдите остальные ошибки и перезапустите экземпляр SQL Server, если он еще не перезапустился самостоятельно.  
  
  
