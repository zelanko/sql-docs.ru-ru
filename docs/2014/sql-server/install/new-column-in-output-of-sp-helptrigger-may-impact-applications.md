---
title: Новый столбец, возвращаемый процедурой sp_helptrigger может повлиять на работу приложений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c7ad878072f8139cc95d6dc34c01f5f48835774a
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2019
ms.locfileid: "59581661"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>Новый столбец, возвращаемый процедурой sp_helptrigger, может повлиять на работу приложений
  последний столбец в наборе результатов, выдаваемых системой sp_helptrigger trigger_schemaias хранимой процедуры.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Чтобы получить сведения о триггерах, определенных для конкретной таблицы, нужно выполнить запрос к представлению каталога sys.triggers.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Проверьте использование в приложениях хранимой процедуры sp_helptrigger. Возможно, придется изменить приложения для обработки дополнительного столбца. Можно также воспользоваться представлением каталога sys.triggers.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
