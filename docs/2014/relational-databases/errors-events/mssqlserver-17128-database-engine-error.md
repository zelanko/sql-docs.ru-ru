---
title: MSSQLSERVER_17128 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c03a181ee815af7b84a5019719c1ff7b532a0198
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169266"
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
  
  
