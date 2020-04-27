---
title: Удалить двоеточие после зарезервированного ключевого слова | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ce2cfce6e35a95b7a07c17c4d3a2fd8a1b1c2610
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093180"
---
# <a name="remove-colon-following-reserved-keyword"></a>Удалите двоеточие после зарезервированного ключевого слова
  Помощник по обновлению обнаружил скрипт, содержащий символ двоеточия (:) после зарезервированного слова. В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]такие синтаксические конструкции пропускаются, а инструкции успешно выполняются. Теперь такой синтаксис приводит к ошибке при выполнении инструкции, если уровень совместимости базы данных установлен в значение 100 или выше.  
  
 Пользовательские базы данных сохраняют свой режим совместимости.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Прежде чем установить для уровня совместимости базы данных значение 100 или более высокое, следует изменить скрипты, убрав двоеточия после зарезервированных ключевых слов. Дополнительные сведения см. в разделе «sp_dbcmptlevel» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
