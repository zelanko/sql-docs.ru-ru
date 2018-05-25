---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7233b624053c2c707e8576ccf4cb23edcec1baa8
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="localdberrorunknownlanguageid"></a>LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|270|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Ошибка при получении локализованного сообщения об ошибке. Язык, указанный параметром «Идентификатор языка», неизвестен.|  
  
## <a name="explanation"></a>Объяснение  
 Запрошенный язык для сообщения об ошибке среды выполнения локальной базы данных неизвестен или не поддерживается.  
  
## <a name="user-action"></a>Действие пользователя  
 Попробуйте запросить один из поддерживаемых языков для сообщений об ошибках среды выполнения локальной базы данных или же язык по умолчанию.  
  
  
