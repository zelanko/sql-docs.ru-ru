---
title: Табличные указания в индексированном представлении определения учитываются в режиме совместимости 80 и запрещены в режиме 90 или более поздней версии | Документация Майкрософт
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
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 93159a8c32f484fd9c734b4847dfd1e7fca854a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317434"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Табличные указания в определении индексированных представлений в режиме совместимости 80 не учитываются, а в режиме совместимости 90 недопустимы
  Табличные указания в определении индексированных представлений не разрешены в режиме совместимости 90 и выше. Дополнительные сведения см. в следующих разделах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] документации: «Разработка индексированных представлений,» «Создание индексированных представлений,» и «указание запроса ([!INCLUDE[tsql](../../includes/tsql-md.md)]).»  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Табличные указания должны быть удалены из определений индексированных представлений. Независимо от используемого режима совместимости рекомендуется провести тестирование приложения. Проверка приложения позволяет убедиться, что оно работает согласно ожиданиям при создании индексированных представлений, их обновлении и доступе к ним, включая сопоставление индексированных представлений с запросами.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
