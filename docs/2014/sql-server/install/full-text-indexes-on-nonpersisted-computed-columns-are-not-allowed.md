---
title: Полнотекстовые индексы для нематериализованных вычисляемых столбцов не разрешены | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 547ce7f80189cc15ea946f5cc8fab470ed83a754
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298282"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>Полнотекстовые индексы для нематериализованных вычисляемых столбцов недопустимы
  Нельзя создавать полнотекстовые индексы на основе недетерминированных и неточных вычисляемых столбцов. Такие столбцы не могут использоваться ни как типизированные, ни в качестве полнотекстовых ключевых столбцов.  
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] полнотекстовый индекс может быть создан с использованием недетерминированных и неточных вычисляемых столбцов в качестве столбцов типа или полнотекстовых ключевых столбцов. Эта функциональность не поддерживается. При обновлении более старые, несовместимые и неподдерживаемые полнотекстовые индексы отключаются.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы включить эти полнотекстовые индексы, измените определения столбцов так, чтобы они стали детерминированными и точными.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
