---
title: INFORMATION_SCHEMA. Возвращает имена схем на СХЕМАХ в базе данных, не баз данных в экземпляре | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0e3683ee043785ec6adc349ac52301280c7bc2b8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094732"
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
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
