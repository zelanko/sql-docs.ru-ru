---
title: Полнотекстовые индексы в базах данных master, tempdb и model не поддерживаются | Документация Майкрософт
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
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c0982614e41097ea51830212e0548efcc42c6ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200754"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Полнотекстовые индексы в базах данных master, tempdb и model не поддерживаются
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не позволяет создавать полнотекстовые индексы для системных баз данных.  
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] полнотекстовые индексы поддерживались в базах данных master, tempdb и model.  
  
 Во время обновления, удаляются все полнотекстовые каталоги в master, tempdb и базы данных модели.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
