---
title: В SQL Server 2005 и SQL Server 2008 Full-Text Search разбиения по словам и фильтры существенно улучшены | Документация Майкрософт
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
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 8d06bda9-0bbf-4baa-b270-07b1c1f640eb
caps.latest.revision: 23
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6a28f0ba9c29be0366b34626fd1c28a7f98c404f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315574"
---
# <a name="full-text-search-word-breakers-and-filters-significantly-improved-in-sql-server-2005-and-sql-server-2008"></a>В SQL Server 2005 и SQL Server 2008 средства разбиения по словам и фильтры полнотекстового поиска были существенно улучшены
  Средства разбиения по словам и фильтры значительно изменились. Были дополнительно улучшены средства разбиения по словам, включая улучшенную поддержку языков и надежность.  
  
## <a name="description"></a>Описание  
 Средства разбиения по словам и фильтры, используемые полнотекстовым поиском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], были значительно изменены для улучшения функциональности и надежности. В некоторых конкретных случаях изменения в средстве разбиения по словам могут повлиять на то, как размечаются некоторые данные. Токены, создаваемые в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], могут отличаться от токенов более ранней версии, созданных в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] или [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Сведения о средства разбиения по словам, см. в разделе [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
