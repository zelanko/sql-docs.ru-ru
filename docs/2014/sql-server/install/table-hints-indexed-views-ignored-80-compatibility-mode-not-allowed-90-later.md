---
title: Табличные указания в индексированном представлении определения учитываются в режиме совместимости 80 и не разрешены в режиме 90 или более поздней версии | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b56e965ecfcfc802457bfa3b5a78118afae5c531
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109857"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Табличные указания в определении индексированных представлений в режиме совместимости 80 не учитываются, а в режиме совместимости 90 недопустимы
  Табличные указания в определении индексированных представлений не разрешены в режиме совместимости 90 и выше. Дополнительные сведения см. в следующих разделах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации: «Разработка индексированных представлений,» «Создание индексированных представлений,» и «указание запроса ([!INCLUDE[tsql](../../includes/tsql-md.md)]).»  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Табличные указания должны быть удалены из определений индексированных представлений. Независимо от используемого режима совместимости рекомендуется провести тестирование приложения. Проверка приложения позволяет убедиться, что оно работает согласно ожиданиям при создании индексированных представлений, их обновлении и доступе к ним, включая сопоставление индексированных представлений с запросами.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
