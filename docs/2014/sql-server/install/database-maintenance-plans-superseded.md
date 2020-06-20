---
title: Планы обслуживания базы данных заменены | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3aea75cc4ecc94ccbaeb1f35cecd0b18ff3a65ff
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054931"
---
# <a name="database-maintenance-plans-superseded"></a>Планы обслуживания базы данных заменены
    
## <a name="component"></a>Компонент  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Агент  
  
## <a name="description"></a>Описание  
 Существующие планы обслуживания базы данных обновлены и продолжают функционировать. Однако нельзя создать новые планы обслуживания базы данных с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Для просмотра планов обслуживания в обозревателе объектов раскройте узел «Управление», а затем «Объекты прежних версий». Можно перенести существующие планы обслуживания базы данных в новый формат, выбрав пункт **перенести** в контекстном меню для любого плана обслуживания базы данных. Поскольку новые функции плана обслуживания не являются прямой заменой планов обслуживания базы данных, некоторые функциональные возможности после миграции могут быть утеряны. При миграции плана обслуживания базы данных старый план не удаляется, поэтому перед удалением старого плана обслуживания можно проверить новый.  
  
 Следующие функции более не поддерживаются планами обслуживания базы данных:  
  
-   доставка журналов;  
  
-   Параметр " **пытаться исправить все незначительные проблемы** " задачи " **Проверка целостности базы данных** "  
  
## <a name="corrective-action"></a>Действие по исправлению  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предотвращает включение доставки журналов в план обслуживания базы данных. Дополнительные сведения см. в разделе «Доставка журналов» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
