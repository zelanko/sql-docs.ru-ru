---
title: MSSQLSERVER_21862 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3abf49fbbf0a41ffe5e8e25995ea6900c8f2f00f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|21862|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21862|  
|Текст сообщения|Столбцы FILESTREAM нельзя опубликовать в публикации с использованием метода синхронизации «database snapshot» или «database snapshot character».|  
  
## <a name="explanation"></a>Объяснение  
Данные FILESTREAM недоступны через моментальный снимок базы данных, поэтому агент моментальных снимков не сможет прочитать данные FILESTREAM, если в качестве метода синхронизации публикации указан параметр *database snapshot* или *database_snapshot_character*.  
  
## <a name="user-action"></a>Действие пользователя  
Измените метод синхронизации публикации на любой другой, кроме *database snapshot* или *database_snapshot_character*, либо просто исключите столбец FILESTREAM из публикации.  
  
