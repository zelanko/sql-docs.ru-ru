---
title: Вложенный триггер AFTER срабатывает даже в том случае, если вложенные триггеры равно OFF | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 826961aef9133c001c643c1ee7058d01438fe868
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098424"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a>Вложенный триггер AFTER срабатывает даже в том случае, если вложенные триггеры отключены
  Советник по переходу обнаружил триггер AFTER, вложенный в триггер INSTEAD OF, который определен для одной или нескольких таблиц. Вложенные триггеры AFTER могут срабатывать, даже если параметр конфигурации сервера `nested triggers` установлен в 0.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Первый триггер AFTER, вложенный в триггер INSTEAD OF, срабатывает, даже если параметру конфигурации сервера `nested triggers` присвоено значение 0. Однако при такой настройке последующие триггеры не срабатывают.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Проверьте приложения на наличие вложенных триггеров, чтобы определить, соответствуют ли приложения бизнес-правилам в случае, если параметру конфигурации сервера `nested triggers` присвоено значение 0, и проведите соответствующие изменения.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
