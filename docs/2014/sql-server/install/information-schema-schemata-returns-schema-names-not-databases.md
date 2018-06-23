---
title: INFORMATION_SCHEMA. Возвращает имена схем на СХЕМЫ в базе данных, не баз данных в экземпляре | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e624597090ab6a7efdb21ebbff6785b1471d7367
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193929"
---
# <a name="informationschemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>Представление INFORMATION_SCHEMA.SCHEMATA возвращает имена схем в базе данных, а не баз данных в экземпляре
  Помощник по обновлению обнаружил инструкции, в которых используется представление INFORMATION_SCHEMA.SCHEMATA. В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это представление возвращало все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и последующих версиях представление возвращает все схемы в базе данных.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представление INFORMATION_SCHEMA.SCHEMATA возвращало все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представление возвращает все схемы в базе данных, что соответствует стандарту языка SQL.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Изменение приложения для ссылки на **sys.databases** представление, чтобы вернуть все базы данных в экземпляре каталога [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
