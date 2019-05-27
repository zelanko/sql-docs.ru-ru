---
title: символ 0xFFFF не является допустимым идентификатором объекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c35c7c65bc312cd20c057b5e2603e7a8f77ce8c8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66096921"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>Символ с кодом 0xFFFF не является допустимым идентификатором объекта
  Помощник по обновлению обнаружил символ 0xFFFF в идентификаторе объекта. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях такие объекты, как базы данных, таблицы и столбцы, идентификаторы которых содержат этот символ, не могут быть переименованы или указаны по ссылке, если для режима совместимости базы данных установлено значение 90 или больше. При обновлении до [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] пользовательские базы данных сохраняют свой режим совместимости. Прежде чем задать для режима совместимости значение 90 или выше, переименуйте объект, который содержит символ 0xFFFF.  
  
 Дополнительные сведения см. в разделе «Идентификаторы» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о режимах совместимости базы данных см. в разделе «sp_dbcmptlevel» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
