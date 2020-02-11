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
ms.openlocfilehash: a4b602d5ff4a94d2888395e6a62f03553fb50f98
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68216377"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Реализация SQLGetDiagRec и SQLGetDiagField
**SQLGetDiagRec** и **SQLGetDiagField** реализуются диспетчером драйверов и каждым драйвером. Диспетчер драйверов и каждый драйвер поддерживают записи диагностики для каждой среды, соединения, инструкции и дескриптора дескриптора, а также освобождают эти записи только при вызове другой функции с этим дескриптором или при освобождении дескриптора.  
  
 Хотя диспетчер драйверов и каждый драйвер должны определить первую запись состояния в соответствии с рейтингом в [последовательности записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md), диспетчер драйверов определяет конечную последовательность записей.  
  
 **SQLGetDiagRec** и **SQLGetDiagField** не помещать диагностические записи о себе.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Правила диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Роль диспетчера драйверов](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Роль драйвера](../../../odbc/reference/develop-app/role-of-the-driver.md)
