---
title: Табличные указания в индексированном представлении определения учитываются в режиме совместимости 80 и запрещены в режиме 90 или более поздней версии | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69a6bae06b1cb5d7a727ff2582f10bccf1e21ca8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091809"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Табличные указания в определении индексированных представлений в режиме совместимости 80 не учитываются, а в режиме совместимости 90 недопустимы
  Табличные указания в определении индексированных представлений не разрешены в режиме совместимости 90 и выше. Дополнительные сведения см. в следующих разделах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] документации: «Конструирование индексированных представлений», «Создание индексированных представлений» и «указание запроса ([!INCLUDE[tsql](../../includes/tsql-md.md)]).»  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Табличные указания должны быть удалены из определений индексированных представлений. Независимо от используемого режима совместимости рекомендуется провести тестирование приложения. Проверка приложения позволяет убедиться, что оно работает согласно ожиданиям при создании индексированных представлений, их обновлении и доступе к ним, включая сопоставление индексированных представлений с запросами.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
