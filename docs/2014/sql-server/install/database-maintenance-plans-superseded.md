---
title: Замененный планы обслуживания базы данных | Документы Microsoft
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
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f71e0cb8cb94cba893403f31cb2ffb9ee229c4ca
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098342"
---
# <a name="database-maintenance-plans-superseded"></a>Планы обслуживания базы данных заменены
    
## <a name="component"></a>Компонент  
 Агент [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Существующие планы обслуживания базы данных обновлены и продолжают функционировать. Однако нельзя создать новые планы обслуживания базы данных с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Для просмотра планов обслуживания в обозревателе объектов раскройте узел «Управление», а затем «Объекты прежних версий». Существующие планы обслуживания базы данных можно перенести в новый формат, выбрав **миграции** в контекстном меню для любого плана обслуживания базы данных. Поскольку новые функции плана обслуживания не являются прямой заменой планов обслуживания базы данных, некоторые функциональные возможности после миграции могут быть утеряны. При миграции плана обслуживания базы данных старый план не удаляется, поэтому перед удалением старого плана обслуживания можно проверить новый.  
  
 Следующие функции более не поддерживаются планами обслуживания базы данных:  
  
-   доставка журналов;  
  
-   **Восстанавливать незначительные повреждения** параметр **Проверка целостности базы данных** задач  
  
## <a name="corrective-action"></a>Действие по исправлению  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предотвращает включение доставки журналов в план обслуживания базы данных. Дополнительные сведения см. в разделе «Доставка журналов» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  