---
title: Поддерживаемые конструкции для хранимых процедур, скомпилированных в собственном виде | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc064eb8a4c6b206d3b690a4c4e7ca196c7475dc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2020
ms.locfileid: "62467878"
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
  
## <a name="security"></a>Безопасность  
 Поддерживаются следующие конструкции:  
  
-   Для процедур: EXECUTE от имени владельца, себя и пользователя.  
  
-   Разрешения GRANT и DENY для таблиц и процедур.  
  
## <a name="see-also"></a>См. также  
 [скомпилированные в собственном коде хранимые процедуры](natively-compiled-stored-procedures.md)  
  
  
