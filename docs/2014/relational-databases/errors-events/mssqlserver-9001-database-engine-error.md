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
ms.openlocfilehash: 0e61894d0d071fbdb36dcfb77895c46c61d0bbd1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85031453"
---
# <a name="mssqlserver_9001"></a>MSSQLSERVER_9001
    
## <a name="details"></a>Сведения  
  
|||  
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
  
  
