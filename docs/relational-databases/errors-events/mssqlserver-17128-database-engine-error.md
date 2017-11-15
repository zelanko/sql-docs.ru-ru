---
title: "MSSQLSERVER_17128 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: a7d0100695085d94c645bb8dae21d10616f3145f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17128|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|INIT_NOBUFSPACE|  
|Текст сообщения|initdata: недостаточно памяти для буферов ядра.|  
  
## <a name="explanation"></a>Объяснение  
Не удается провести начальное выделение памяти из буферного пула или резервирование памяти. SQL Server завершает работу.  
  
## <a name="user-action"></a>Действие пользователя  
Эта обычно случается при запуске SQL Server на очень маломощном компьютере, параметры которого не достигают минимальных требований к системе.  
  
