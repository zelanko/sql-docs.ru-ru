---
title: Вложенный триггер AFTER срабатывает, даже если вложенность триггера ОТКЛЮЧЕНа | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0675c412d753a1ce60fa41c7ced40528b3c58f75
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093830"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a>Вложенный триггер AFTER срабатывает даже в том случае, если вложенные триггеры отключены
  Советник по переходу обнаружил триггер AFTER, вложенный в триггер INSTEAD OF, который определен для одной или нескольких таблиц. Вложенные триггеры AFTER могут срабатывать, даже если параметр конфигурации сервера `nested triggers` установлен в 0.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Первый триггер AFTER, вложенный в триггер INSTEAD OF, срабатывает, даже если параметру конфигурации сервера `nested triggers` присвоено значение 0. Однако при такой настройке последующие триггеры не срабатывают.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Проверьте приложения на наличие вложенных триггеров, чтобы определить, соответствуют ли приложения бизнес-правилам в случае, если параметру конфигурации сервера `nested triggers` присвоено значение 0, и проведите соответствующие изменения.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
