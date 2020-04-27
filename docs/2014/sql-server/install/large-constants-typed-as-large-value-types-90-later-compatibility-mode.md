---
title: Большие константы вводятся как типы больших значений в режиме совместимости 90 или более поздней версии | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c7aded5577e28d94f42e108e46bb8a9c3cd6020
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094093"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a>В режиме совместимости 90 и выше большие константы имеют тип больших значений
  Помощник по обновлению обнаружил большие константы. Символьные строковые константы и двоичные константы размером более 8000 байт в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] рассматриваются как типы данных больших объектов. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях большие символьные и двоичные константы, а также константы в Юникоде, имеют тип больших значений.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Если строковые функции, например CHARINDEX или PATINDEX, используются со строковыми или двоичными константами размером более 8000 байт, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] возвращает ошибку с номером 8116, а [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии — ошибку с номером 8152.  
  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]строковые функции возвращают ошибку 8116, если они используются с типами `text`данных `ntext`, и `image` .  
  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях большие константы рассматриваются как типы данных `varchar(max)`, `nvarchar(max)` и `varbinary(max)` соответственно. Эти типы данных совместимы со строковыми функциями.  
  
 В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях строковые функции, такие как CHARINDEX и PATINDEX, предполагают, что размер найденной строки менее 8000 байт. Поэтому CHARINDEX и PATINDEX формируют ошибку 8152.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
