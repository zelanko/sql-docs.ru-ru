---
title: Невозможно обновить базы данных, которые доступны только для чтения | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ba48ed2bd80961a4949dc13f04fed0637ecc27ec
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054683"
---
# <a name="read-only-databases-cannot-be-upgraded"></a>Доступные только для чтения базы данных не могут быть обновлены
  Помощник по обновлению определил, что некоторые базы данных в этом экземпляре служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не могут быть обновлены.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Обнаружена база данных, доступная только для чтения. Чтобы обновить базу данных, программа установки должна иметь возможность записи в базу данных.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если база данных не используется, используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Диспетчер Enterprise Manager, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] или ИНСТРУКЦИю ALTER DATABASE, чтобы изменить базу данных на чтение и запись. Следующая инструкция переводит базу данных в режим чтения и записи.  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 Дополнительные сведения об инструкции ALTER DATABASE см. в разделе «ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
