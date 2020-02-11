---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d95d3e67fdcd7159074e2f20ffa558f4c80bbcb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036355"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Сопоставление типов сведений атрибутов1 курсора
При использовании ODBC 3. Приложение *x* вызывает **SQLGetInfo** в драйвере ODBC 2 *. x* с типом сведений SQL_XXXX_CURSOR_ATTRIBUTES1 (для динамических, однопроходных, набора ключей-драйверов или статических курсоров). Настройка битов, возвращаемых диспетчером драйверов, зависит от того, что такое ODBC 2. драйвер *x* возвращает для соответствующего ODBC 2. *x* сведения о типах данных. Биты задаются, как показано в следующей таблице.  
  
|Бит в<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Тип курсора|ODBC 2. *x* информация<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|All|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dynamic, набор ключей-Driver, статический|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dynamic, набор ключей-Driver, статический|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|All|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dynamic, набор ключей-Driver, статический|SQL_POS_OPERATIONS|
