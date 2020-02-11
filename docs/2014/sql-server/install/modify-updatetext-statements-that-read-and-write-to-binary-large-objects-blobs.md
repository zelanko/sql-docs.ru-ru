---
title: Изменение инструкций UPDATETEXT, считывающих и записывающих данные в большие двоичные объекты (BLOB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f2f3c8af333cc20398e7951bd6fd53433da0288c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093770"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>Внесите изменения в инструкции UPDATETEXT, которые считывают и записывают большие двоичные объекты
  Помощник по обновлению обнаружил инструкции UPDATETEXT, которые читают и записывают одни и те же большие двоичные объекты (BLOB) с использованием одного и того же текстового указателя. 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает подобное использование текстовых указателей.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Скопируйте большой двоичный объект во временную таблицу или табличную переменную, а затем присвойте это значение исходному столбцу.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
