---
title: ДЛЯ ОБЗОРА не допускается в представлениях в режиме совместимости 90 и выше | Документация Майкрософт
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
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
caps.latest.revision: 13
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b309f79379bacbca6cfc4d3b134b31ead8e9e506
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247924"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a>Предложение FOR BROWSE не поддерживается для представлений в режиме совместимости 90 и выше
  Помощник по обновлению обнаружил в представлении предложение FOR BROWSE. Предложение FOR BROWSE допускается (и не учитывается) в представлениях, если для базы данных задан режим совместимости 80. Предложение FOR BROWSE недопустимо в представлениях, если для базы данных задан режим совместимости 90 и выше.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 При обновлении пользовательские базы данных сохраняют свой режим совместимости. До изменения режима совместимости базы данных на 90 или выше следует удалить из определений представлений предложение FOR BROWSE. Дополнительные сведения см. в разделе «sp_dbcmptlevel» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
