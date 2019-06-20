---
title: Отзыв и предоставление прав при использовании хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e881201e4653a168faff2fa438be19c1ca37e9b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127969"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Отзыв и предоставление прав при использовании хранимых процедур
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер Microsoft ODBC для Oracle возвращает следующее сообщение об ошибке при предоставляются права пользователя и затем отменены для таблицы, получить доступ с помощью хранимой процедуры:  
  
 = ЗНАЧЕНИЕ SQL_ERROR-1.  
  
 szErrorMsg = «[Microsoft] [драйвер ODBC для Oracle] неверное число параметров»  
  
 szErrorMsg = «[Microsoft] [драйвер ODBC для Oracle] синтаксическая ошибка или нарушение доступа»  
  
 Вызов функции Oracle OCI Odessp() происходит сбой в этом сценарии, но необходимы для реализации параметров по умолчанию. После изменения основных разрешений таблицы, хранимой процедуры должны быть перекомпилированы перед повторным запуском.
