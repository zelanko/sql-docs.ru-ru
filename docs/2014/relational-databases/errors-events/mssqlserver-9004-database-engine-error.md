---
title: MSSQLSERVER_9004 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 08cf49c351df3b1130fea55e2d34f7fa7bcbd890
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86550786"
---
# <a name="mssqlserver_9004"></a>MSSQLSERVER_9004
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
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
  
  
