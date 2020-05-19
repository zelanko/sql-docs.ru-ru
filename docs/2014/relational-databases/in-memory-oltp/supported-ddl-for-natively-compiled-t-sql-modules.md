---
title: Поддерживаемые конструкции для хранимых процедур, скомпилированных в собственном виде | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0c439a424c409522eee696d0161c94251e82fb35
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718819"
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
  
  
