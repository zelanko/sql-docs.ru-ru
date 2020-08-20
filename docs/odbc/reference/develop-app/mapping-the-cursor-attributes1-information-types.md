---
description: Сопоставление типов сведений атрибутов1 курсора
title: Сопоставление типов сведений Attributes1 курсора | Документация Майкрософт
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
ms.openlocfilehash: fcd4c1eaa6ddd2e6db4f2634cc22d3148e7977cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461406"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Сопоставление типов сведений атрибутов1 курсора
При использовании ODBC 3. Приложение *x* вызывает **SQLGetInfo** в драйвере ODBC 2 *. x* с типом сведений SQL_XXXX_CURSOR_ATTRIBUTES1 (для динамических, однопроходных, набора ключей-драйверов или статических курсоров). Настройка битов, возвращаемых диспетчером драйверов, зависит от того, что такое ODBC 2. драйвер *x* возвращает для соответствующего ODBC 2. *x* сведения о типах данных. Биты задаются, как показано в следующей таблице.  
  
|Бит в<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Тип курсора|ODBC 2. *x* информация<br /><br /> тип|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|Все|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dynamic, набор ключей-Driver, статический|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dynamic, набор ключей-Driver, статический|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|Все|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dynamic, набор ключей-Driver, статический|SQL_POS_OPERATIONS|
