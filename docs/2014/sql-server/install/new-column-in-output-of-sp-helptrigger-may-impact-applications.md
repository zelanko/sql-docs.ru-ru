---
title: Новый столбец в выходных данных sp_helptrigger может повлиять на работу приложений | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d62b9b9546fa113557bf962d68876d8c55a71ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097647"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>Новый столбец, возвращаемый процедурой sp_helptrigger, может повлиять на работу приложений
  последний столбец в результирующем наборе возвращается системой sp_helptrigger trigger_schemaias хранимой процедуры.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Чтобы получить сведения о триггерах, определенных для конкретной таблицы, нужно выполнить запрос к представлению каталога sys.triggers.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Проверьте использование в приложениях хранимой процедуры sp_helptrigger. Возможно, придется изменить приложения для обработки дополнительного столбца. Можно также воспользоваться представлением каталога sys.triggers.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
