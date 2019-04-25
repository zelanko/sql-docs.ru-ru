---
title: Реализация SQLGetDiagRec и SQLGetDiagField | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab1f808b005afaa91ed93bf8f8ec7a8385c9c945
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447288"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Реализация SQLGetDiagRec и SQLGetDiagField
**SQLGetDiagRec** и **SQLGetDiagField** реализуются путем диспетчера драйверов и каждого драйвера. Диспетчер драйверов каждого драйвера обслуживания диагностических записей для каждой среды, подключения, инструкции и дескриптора и освободить записи только в том случае, когда будет вызвана другая функция с маркер или дескриптор освобождается.  
  
 Несмотря на то, что диспетчер драйверов и каждого драйвера необходимо определить первую запись состояния в соответствии с рейтингами в [последовательность записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md), результирующая последовательность записей определяет диспетчера драйверов.  
  
 **SQLGetDiagRec** и **SQLGetDiagField** не размещайте диагностические записи о себе.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Правила диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Роль диспетчера драйверов](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Роль драйвера](../../../odbc/reference/develop-app/role-of-the-driver.md)
