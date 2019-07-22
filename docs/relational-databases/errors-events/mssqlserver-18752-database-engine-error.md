---
title: MSSQLSERVER_18752 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 18752 (Database Engine error)
ms.assetid: 234c58d8-7a1e-4b07-a64b-32a311527980
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8aa5f3a75c4d21e148d50fe71b75a21a287a2a2b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68137039"
---
# <a name="mssqlserver18752"></a>MSSQLSERVER_18752
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|18752|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REPL_INUSE|  
|Текст сообщения|К базе данных одновременно может быть подключен лишь один агент чтения журнала или процедура, относящаяся к журналу (sp_repldone, sp_replcmds и sp_replshowcmds). Если выполняется процедура, относящаяся к журналу, удалите подключение, по которому выполнялась процедура, или выполните для этого подключения процедуру sp_replflush, прежде чем запустить агент чтения журнала или выполнить другую процедуру, относящуюся к журналу.|  
  
## <a name="explanation"></a>Объяснение  
К базе данных одновременно может быть подключен лишь один агент чтения журнала или одна процедура, относящаяся к журналу.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что в той же базе данных публикаций не запущен еще один агент чтения журнала и все активные соединения после запуска процедуры sp_replcmds или sp_repltrans, или sp_repldone либо запускают процедуру sp_replflush, либо разрываются.  
  
