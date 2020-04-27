---
title: MSSQLSERVER_18752 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5e65a05d590ca3492d1330d66fbc6bdfda8324b5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915090"
---
# <a name="mssqlserver_18752"></a>MSSQLSERVER_18752
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|18752|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REPL_INUSE|  
|Текст сообщения|К базе данных одновременно может быть подключен лишь один агент чтения журнала или процедура, относящаяся к журналу (sp_repldone, sp_replcmds и sp_replshowcmds). Если выполняется процедура, относящаяся к журналу, удалите подключение, по которому выполнялась процедура, или выполните для этого подключения процедуру sp_replflush, прежде чем запустить агент чтения журнала или выполнить другую процедуру, относящуюся к журналу.|  
  
## <a name="explanation"></a>Объяснение  
 К базе данных одновременно может быть подключен лишь один агент чтения журнала или одна процедура, относящаяся к журналу.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что в той же базе данных публикаций не запущен еще один агент чтения журнала и все активные соединения после запуска процедуры sp_replcmds или sp_repltrans, или sp_repldone либо запускают процедуру sp_replflush, либо разрываются.  
  
  
