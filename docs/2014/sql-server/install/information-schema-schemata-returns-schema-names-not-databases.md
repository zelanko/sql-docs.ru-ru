---
title: INFORMATION_SCHEMA. SCHEMATA возвращает имена схем в базе данных, а не базы данных в экземпляре | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094732"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>Представление INFORMATION_SCHEMA.SCHEMATA возвращает имена схем в базе данных, а не баз данных в экземпляре
  Помощник по обновлению обнаружил инструкции, в которых используется представление INFORMATION_SCHEMA.SCHEMATA. В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это представление возвращало все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и последующих версиях представление возвращает все схемы в базе данных.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представление INFORMATION_SCHEMA.SCHEMATA возвращало все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представление возвращает все схемы в базе данных, что соответствует стандарту языка SQL.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените приложение, чтобы оно ссылалось на представление каталога **sys. databases** , чтобы возвращались все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]базы данных в экземпляре.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
