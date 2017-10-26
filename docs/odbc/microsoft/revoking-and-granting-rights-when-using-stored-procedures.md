---
title: "Отмена и предоставление прав, при использовании хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 67bad57e201d10c5eb29aafb19fa9f513c43b172
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Отзыв и предоставление прав при использовании хранимых процедур
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер ODBC для Oracle возвращает следующее сообщение об ошибке при предоставляются права пользователя и затем отозван на таблицу, доступ с помощью хранимой процедуры:  
  
 ЗНАЧЕНИЕ SQL_ERROR = 1  
  
 szErrorMsg = «[Microsoft] [драйвер ODBC для Oracle] неверное число параметров»  
  
 szErrorMsg = «[Microsoft] [драйвер ODBC для Oracle] синтаксическая ошибка или нарушение доступа»  
  
 Вызов функции Oracle OCI Odessp() завершается ошибкой в этом сценарии, но необходимо для реализации параметров по умолчанию. После изменения базовой таблицы разрешения хранимая процедура перекомпилируется перед повторным запуском.

