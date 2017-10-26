---
title: "MSSQLSERVER_611 | Документация Майкрософт"
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
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b96bc69d694f4831086804cec2fe655c113e9d89
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|611|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|VAR_SIZE_TOO_BIG|  
|Текст сообщения|Не удается добавить или обновить строку, поскольку суммарный размер переменных столбцов с учетом дополнительной памяти превысил допустимый на %d байт.|  
  
## <a name="explanation"></a>Объяснение  
Максимальный размер переменного столбца превышает размер, определенный схемой. Ошибка 611 возвращается при превышении размера столбца переменной, когда разрешен формат хранения vardecimal, либо если его размер превышает максимально допустимый в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для записи со сжатием данных.  
  
## <a name="user-action"></a>Действие пользователя  
Уменьшите размер записи.  
  

