---
title: "MSSQLSERVER_9004 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 8c794316e9995e4a61fd0af55318c411dbcbda61
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9004|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LOG_CORRUPT|  
|Текст сообщения|Произошла ошибка при обработке журнала для базы данных "%.*ls".  Если возможно, восстановите из резервной копии. Если резервная копия недоступна, возможно, понадобится перестроить журнал.|  
  
## <a name="explanation"></a>Объяснение  
Во время обработки журнала возникла ошибка при выполнении операции отката, восстановления или репликации. Это может указывать либо на обнаруженную операционной системой ошибку, либо на ошибку внутренней согласованности, обнаруженную [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Действие пользователя  
Одно из следующих действий исправит эту ошибку.  
  
-   Восстановление из резервной копии.  
  
-   Перестроение журнала.  
  
Также проверьте системные события и журналы ошибок для определения неполадок в системе, которые могут являться причиной проблемы.  
  
