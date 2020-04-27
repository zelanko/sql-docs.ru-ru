---
title: Полнотекстовые индексы баз данных master, tempdb и Model не поддерживаются | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 743c7153b034cf5e1267c6a0da1e585845800980
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095200"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Полнотекстовые индексы в базах данных master, tempdb и model не поддерживаются
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не позволяет создавать полнотекстовые индексы для системных баз данных.  
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] полнотекстовые индексы поддерживались в базах данных master, tempdb и model.  
  
 Все полнотекстовые каталоги в базах данных master, tempdb и Model удаляются во время обновления.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
