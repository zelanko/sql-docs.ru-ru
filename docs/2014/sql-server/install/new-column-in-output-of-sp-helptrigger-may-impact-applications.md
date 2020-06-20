---
title: Новый столбец в выходных данных sp_helptrigger может повлиять на приложения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012171"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a>Новый столбец, возвращаемый процедурой sp_helptrigger, может повлиять на работу приложений
  trigger_schemaias последний столбец в результирующем наборе, возвращенном системной хранимой процедурой sp_helptrigger.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Чтобы получить сведения о триггерах, определенных для конкретной таблицы, нужно выполнить запрос к представлению каталога sys.triggers.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Проверьте использование в приложениях хранимой процедуры sp_helptrigger. Возможно, придется изменить приложения для обработки дополнительного столбца. Можно также воспользоваться представлением каталога sys.triggers.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
