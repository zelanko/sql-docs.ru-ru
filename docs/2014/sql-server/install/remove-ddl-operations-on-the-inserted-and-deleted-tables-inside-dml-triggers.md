---
title: Удалите DDL-операции в таблицах inserted и deleted внутри триггеров DML | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b2f0990fbe65adc97b9e654f6393e25582363596
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093131"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a>Удалите DDL-операции в таблицах inserted и deleted внутри триггеров DML
  Инструкции языка DDL определения данных, такие как CREATE INDEX не может выполняться в таблицах inserted и deleted внутри триггеров DML. Некоторые инструкции языка DDL для таблиц inserted и deleted допускались в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе «Использование таблиц inserted и deleted» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите любые DDL-операции, которые применяются к вставленным и удаленным таблицам внутри триггеров DML.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
