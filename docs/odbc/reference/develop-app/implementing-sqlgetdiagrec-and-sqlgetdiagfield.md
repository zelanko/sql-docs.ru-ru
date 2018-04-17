---
title: Реализация SQLGetDiagRec и SQLGetDiagField | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.workload: Inactive
ms.openlocfilehash: e4eda963538e6f5acb884e494a8c8a3dd533bf70
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Реализация SQLGetDiagRec и SQLGetDiagField
**SQLGetDiagRec** и **SQLGetDiagField** реализуются диспетчера драйверов и каждого драйвера. Диспетчер драйверов драйверу Ведение диагностические записи для каждой среды, подключения, инструкции и дескриптора и освободить эти записи только в том случае, если будет вызвана другая функция с дескриптором или дескриптор освобождается.  
  
 Несмотря на то, что диспетчер драйверов и каждого из драйверов необходимо определить, первая запись состояния в соответствии с рейтингами в [последовательности записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md), результирующая последовательность записей определяет диспетчера драйверов.  
  
 **SQLGetDiagRec** и **SQLGetDiagField** не размещайте диагностические записи о себе.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Правила диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Роль диспетчера драйверов](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Роль драйвера](../../../odbc/reference/develop-app/role-of-the-driver.md)
