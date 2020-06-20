---
title: Табличные указания в определениях индексированных представлений игнорируются в режиме совместимости 80 и не разрешены в режиме 90 или более поздней версии | Документация Майкрософт
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
ms.openlocfilehash: cf3cb2b06dc477d93c8fd42312b4835ded42afb4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85035954"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Табличные указания в определении индексированных представлений в режиме совместимости 80 не учитываются, а в режиме совместимости 90 недопустимы
  Табличные указания в определении индексированных представлений не разрешены в режиме совместимости 90 и выше. Дополнительные сведения см. в следующих разделах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации: «проектирование индексированных представлений», «создание индексированных представлений» и «указание запроса ( [!INCLUDE[tsql](../../includes/tsql-md.md)] )».  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Табличные указания должны быть удалены из определений индексированных представлений. Независимо от используемого режима совместимости рекомендуется провести тестирование приложения. Проверка приложения позволяет убедиться, что оно работает согласно ожиданиям при создании индексированных представлений, их обновлении и доступе к ним, включая сопоставление индексированных представлений с запросами.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
