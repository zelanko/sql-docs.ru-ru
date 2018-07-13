---
title: INFORMATION_SCHEMA. Возвращает имена схем на СХЕМАХ в базе данных, не баз данных в экземпляре | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c32683c6dc6aaa26079443d2ff4bc5d1f0994d76
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198444"
---
# <a name="informationschemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>Представление INFORMATION_SCHEMA.SCHEMATA возвращает имена схем в базе данных, а не баз данных в экземпляре
  Помощник по обновлению обнаружил инструкции, в которых используется представление INFORMATION_SCHEMA.SCHEMATA. В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это представление возвращало все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и последующих версиях представление возвращает все схемы в базе данных.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представление INFORMATION_SCHEMA.SCHEMATA возвращало все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представление возвращает все схемы в базе данных, что соответствует стандарту языка SQL.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Изменить приложение, чтобы ссылаться на **sys.databases** представления, чтобы вернуть все базы данных в экземпляре каталога [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
