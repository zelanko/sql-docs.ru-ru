---
title: MSSQLSERVER_9004 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe4aa3b74af774543c5125652d8f860c68fb04fd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68118326"
---
# <a name="mssqlserver_9004"></a>MSSQLSERVER_9004
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
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
  
