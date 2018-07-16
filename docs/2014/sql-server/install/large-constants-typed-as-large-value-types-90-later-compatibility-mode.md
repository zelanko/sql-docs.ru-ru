---
title: Большие константы имеют тип больших значений в режиме совместимости 90 и выше | Документация Майкрософт
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
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 59f9afc3c8f083da2c1d3934d5aea5b541c6c527
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257770"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a>В режиме совместимости 90 и выше большие константы имеют тип больших значений
  Помощник по обновлению обнаружил большие константы. Символьные строковые константы и двоичные константы размером более 8000 байт в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] рассматриваются как типы данных больших объектов. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях большие символьные и двоичные константы, а также константы в Юникоде, имеют тип больших значений.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Если строковые функции, например CHARINDEX или PATINDEX, используются со строковыми или двоичными константами размером более 8000 байт, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] возвращает ошибку с номером 8116, а [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии — ошибку с номером 8152.  
  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], строковые функции возвращают ошибку 8116 при их использовании с `text`, `ntext`, и `image` типы данных.  
  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях большие константы рассматриваются как типы данных `varchar(max)`, `nvarchar(max)` и `varbinary(max)` соответственно. Эти типы данных совместимы со строковыми функциями.  
  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях строковые функции, такие как CHARINDEX и PATINDEX, предполагают, что размер найденной строки менее 8000 байт. Поэтому CHARINDEX и PATINDEX формируют ошибку 8152.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
