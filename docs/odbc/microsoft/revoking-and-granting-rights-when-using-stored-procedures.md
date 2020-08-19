---
description: Отзыв и предоставление прав при использовании хранимых процедур
title: Отмена и предоставление прав при использовании хранимых процедур | Документация Майкрософт
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
ms.openlocfilehash: ad59f18f040dd1fefec606c99e3cce5f1002c22a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449276"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Отзыв и предоставление прав при использовании хранимых процедур
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Драйвер Microsoft ODBC для Oracle возвращает следующее сообщение об ошибке при предоставлении и отмене прав пользователя для таблицы, к которой обращается хранимая процедура:  
  
 SQL_ERROR =-1  
  
 Сзеррормсг = "[Microsoft] [драйвер ODBC для Oracle] неправильное число параметров"  
  
 Сзеррормсг = "[Microsoft] [драйвер ODBC для Oracle] синтаксическая ошибка или нарушение прав доступа"  
  
 Вызов функции Oracle OCI Одессп () завершается ошибкой в этом сценарии, но он необходим для реализации параметров по умолчанию. После изменения разрешений базовой таблицы хранимая процедура должна быть перекомпилирована перед повторным запуском.
