---
title: Отмена и предоставление прав при использовании сохраненных процедур (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 469e6f0fdc6794e3bd163844e43821798aa4a617
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303990"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Отзыв и предоставление прав при использовании хранимых процедур
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Драйвер Microsoft ODBC для Oracle возвращает следующее сообщение об ошибке, когда права пользователя предоставляются, а затем аннулируется на столе, доступ к которой сопровождается сохраненной процедурой:  
  
 SQL_ERROR-1  
  
 szErrorMsg» (Microsoft) драйвер ODBC для Oracle»Неправильное количество параметров»  
  
 szErrorMsg» (Microsoft) драйвер ODBC для ошибки Oracle или нарушения доступа»  
  
 Вызов функции Oracle OCI Odessp() не удается в этом сценарии, но необходим для реализации параметров по умолчанию. После изменения базовых разрешений таблицы необходимо перекомпилировать процедуру хранения перед запуском.
