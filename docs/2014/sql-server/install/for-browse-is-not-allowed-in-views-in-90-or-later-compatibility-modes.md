---
title: ДЛЯ обзора не допускается в представлениях в режиме совместимости 90 или более поздней версии | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4811a3df80257b1e2d0e903fad562568eeec4ea2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095175"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a>Предложение FOR BROWSE не поддерживается для представлений в режиме совместимости 90 и выше
  Помощник по обновлению обнаружил в представлении предложение FOR BROWSE. Предложение FOR BROWSE допускается (и не учитывается) в представлениях, если для базы данных задан режим совместимости 80. Предложение FOR BROWSE недопустимо в представлениях, если для базы данных задан режим совместимости 90 и выше.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 При обновлении пользовательские базы данных сохраняют свой режим совместимости. До изменения режима совместимости базы данных на 90 или выше следует удалить из определений представлений предложение FOR BROWSE. Дополнительные сведения см. в разделе «sp_dbcmptlevel» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
