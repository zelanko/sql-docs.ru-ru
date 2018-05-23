---
title: MSSQLSERVER_9004 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e3adf2903a0b8b0861f9a773531d5fea1b6bff5a
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
