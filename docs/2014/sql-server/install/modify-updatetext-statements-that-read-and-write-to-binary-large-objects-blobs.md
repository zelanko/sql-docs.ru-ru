---
title: Измените инструкции UPDATETEXT, которые считывают и записывают большие двоичные объекты (BLOB) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5b0c6df5c9324a35f1f642d366ef8f2780341592
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189904"
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
  
  
