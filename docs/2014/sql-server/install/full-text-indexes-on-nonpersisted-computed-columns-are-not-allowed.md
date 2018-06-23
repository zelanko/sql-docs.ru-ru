---
title: Полнотекстовые индексы для нематериализованных вычисляемых столбцов недопустимы. | Документы Microsoft
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
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d51500dca40ed039816b973cb4698971996e2b01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188959"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>Полнотекстовые индексы для нематериализованных вычисляемых столбцов недопустимы
  Нельзя создавать полнотекстовые индексы на основе недетерминированных и неточных вычисляемых столбцов. Такие столбцы не могут использоваться ни как типизированные, ни в качестве полнотекстовых ключевых столбцов.  
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] полнотекстовый индекс может быть создан с использованием недетерминированных и неточных вычисляемых столбцов в качестве столбцов типа или полнотекстовых ключевых столбцов. Эта функциональность не поддерживается. При обновлении более старые, несовместимые и неподдерживаемые полнотекстовые индексы отключаются.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы включить эти полнотекстовые индексы, измените определения столбцов так, чтобы они стали детерминированными и точными.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  