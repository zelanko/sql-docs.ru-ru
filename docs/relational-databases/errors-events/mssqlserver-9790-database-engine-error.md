---
title: "MSSQLSERVER_9790 | Документация Майкрософт"
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
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f7a07e157da848a3201d0a50d6e270988ddf9943
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9790|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Текст сообщения|Не удалось найти маршрут для входящего сообщения. Системная база данных MSDB, содержащая сведения о маршрутах, находится в режиме SINGLE USER.|  
  
## <a name="explanation"></a>Объяснение  
Произошла ошибка при попытке определения категории сообщения, полученного в автономном режиме, поскольку база данных MSDB находилась в однопользовательском режиме.  
  
## <a name="user-action"></a>Действие пользователя  
С помощью команды ALTER DATABASE измените режим MSDB на MULTI USER.  
  

