---
title: Реализация SQLGetDiagRec и SQLGetDiagField | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a6be0d20a2e1171275c3a1ef05d83383a10b763
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Реализация SQLGetDiagRec и SQLGetDiagField
**SQLGetDiagRec** и **SQLGetDiagField** реализуются диспетчера драйверов и каждого драйвера. Диспетчер драйверов драйверу Ведение диагностические записи для каждой среды, подключения, инструкции и дескриптора и освободить эти записи только в том случае, если будет вызвана другая функция с дескриптором или дескриптор освобождается.  
  
 Несмотря на то, что диспетчер драйверов и каждого из драйверов необходимо определить, первая запись состояния в соответствии с рейтингами в [последовательности записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md), результирующая последовательность записей определяет диспетчера драйверов.  
  
 **SQLGetDiagRec** и **SQLGetDiagField** не размещайте диагностические записи о себе.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Правила диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Роль диспетчера драйверов](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Роль драйвера](../../../odbc/reference/develop-app/role-of-the-driver.md)
