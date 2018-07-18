---
title: Поддерживаемые конструкции для скомпилированных в собственном коде хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6cdd5c7d154f1841aa5c90e110a596d8684a535
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233274"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a>Поддерживаемые конструкции для хранимых процедур, скомпилированных в собственном коде
  В этом разделе перечислены поддерживаемые конструкции в хранимых процедурах, скомпилированных в собственном коде.  
  
 Дополнительные сведения о неподдерживаемых конструкциях см. в разделе [Конструкции языка Transact-SQL, не поддерживаемые в In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="procedure-ddl"></a>Процедура DDL  
 Поддерживаются следующие конструкции:  
  
-   CREATE PROCEDURE  
  
-   DROP PROCEDURE  
  
-   SCHEMABINDING (требуется для хранимых процедур, скомпилированных в собственном коде)  
  
-   NATIVE_COMPILATION  
  
-   Параметры могут быть объявлены как NOT NULL.  
  
-   Возвращающие табличные значения параметры  
  
## <a name="security"></a>безопасность  
 Поддерживаются следующие конструкции:  
  
-   Для процедур: выполнение AS OWNER, SELF и пользователя.  
  
-   Разрешения GRANT и DENY для таблиц и процедур.  
  
## <a name="see-also"></a>См. также  
 [Скомпилированные в собственном коде хранимые процедуры](natively-compiled-stored-procedures.md)  
  
  
