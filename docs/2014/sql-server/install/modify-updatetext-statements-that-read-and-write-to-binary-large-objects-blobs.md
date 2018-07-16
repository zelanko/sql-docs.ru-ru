---
title: Измените инструкции UPDATETEXT, которые считывают и записывают большие двоичные объекты (BLOB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 85036a4d91fc426a0195c4fd589fbddcadfb5da4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37234334"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>Внесите изменения в инструкции UPDATETEXT, которые считывают и записывают большие двоичные объекты
  Помощник по обновлению обнаружил инструкции UPDATETEXT, которые читают и записывают одни и те же большие двоичные объекты (BLOB) с использованием одного и того же текстового указателя. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает подобное использование текстовых указателей.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Скопируйте большой двоичный объект во временную таблицу или табличную переменную, а затем присвойте это значение исходному столбцу.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
