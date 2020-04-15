---
title: Картирование атрибутов Курсора1 Типы информации (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d70cf0a93a6c6160faeb0afe991b2adfff11b8f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301047"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Сопоставление типов сведений атрибутов1 курсора
Когда ODBC 3. *приложение вызывает* **s'LGetInfo** в драйвере ODBC 2 *.x* с SQL_XXXX_CURSOR_ATTRIBUTES1 типом информации (для динамических, только для нас только ключей, драйверов ключей или статических курсоров), настройка битов, возвращенных менеджером драйвера, зависит от того, что такое ODBC 2. *x* возврат драйвера для соответствующего ODBC 2. *х* типы информации. Биты устанавливаются как показано в следующей таблице.  
  
|Бит в<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Тип курсора|ODBC 2. *x* информация<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|Все|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Динамический, драйвер клавиш, статический|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Динамический, драйвер клавиш, статический|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|Все|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Динамический, драйвер клавиш, статический|SQL_POS_OPERATIONS|
