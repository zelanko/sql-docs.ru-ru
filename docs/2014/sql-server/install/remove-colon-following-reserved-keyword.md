---
title: Удалить следующие двоеточие зарезервированное ключевое слово | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
caps.latest.revision: 11
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5969fdcd95f0168dad587552bc114f874a3feeef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282580"
---
# <a name="remove-colon-following-reserved-keyword"></a>Удалите двоеточие после зарезервированного ключевого слова
  Помощник по обновлению обнаружил скрипт, содержащий символ двоеточия (:) после зарезервированного слова. В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] такие синтаксические конструкции пропускаются, а инструкции успешно выполняются. Теперь такой синтаксис приводит к ошибке при выполнении инструкции, если уровень совместимости базы данных установлен в значение 100 или выше.  
  
 Пользовательские базы данных сохраняют свой режим совместимости.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Прежде чем установить для уровня совместимости базы данных значение 100 или более высокое, следует изменить скрипты, убрав двоеточия после зарезервированных ключевых слов. Дополнительные сведения см. в разделе «sp_dbcmptlevel» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
