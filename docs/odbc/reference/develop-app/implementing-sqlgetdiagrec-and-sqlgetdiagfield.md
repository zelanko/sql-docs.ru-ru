---
title: "Реализация SQLGetDiagRec и SQLGetDiagField | Документы Microsoft"
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 463ddfe552c94a9e90ceb2a24f8061674955979d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Реализация SQLGetDiagRec и SQLGetDiagField
**SQLGetDiagRec** и **SQLGetDiagField** реализуются диспетчера драйверов и каждого драйвера. Диспетчер драйверов драйверу Ведение диагностические записи для каждой среды, подключения, инструкции и дескриптора и освободить эти записи только в том случае, если будет вызвана другая функция с дескриптором или дескриптор освобождается.  
  
 Несмотря на то, что диспетчер драйверов и каждого из драйверов необходимо определить, первая запись состояния в соответствии с рейтингами в [последовательности записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md), результирующая последовательность записей определяет диспетчера драйверов.  
  
 **SQLGetDiagRec** и **SQLGetDiagField** не размещайте диагностические записи о себе.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Правила обработки диагностики](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Роли диспетчера драйверов](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Роль драйвера](../../../odbc/reference/develop-app/role-of-the-driver.md)
