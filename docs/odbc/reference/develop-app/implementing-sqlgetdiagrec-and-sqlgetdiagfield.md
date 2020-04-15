---
title: Внедрение S'LGetDiagRec и S'LGetDiagField Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c090af19a9296e46e3036ca23f6c97298bcb1b8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300144"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Реализация SQLGetDiagRec и SQLGetDiagField
Менеджер драйверов и каждый водитель внедряют проекты **s'LGetDiagRec** и **S'LGetDiagField.** Менеджер драйвера и каждый драйвер ведут диагностические записи для каждой среды, соединения, оператора и дескриптора, и освобождают эти записи только тогда, когда другая функция вызывается с этой ручкой или ручка освобождается.  
  
 Хотя и менеджер драйвера, и каждый водитель должны определить первую запись статуса в соответствии с рейтингом в [последовательности записей статуса,](../../../odbc/reference/develop-app/sequence-of-status-records.md)менеджер драйвера определяет окончательную последовательность записей.  
  
 **СЗЛГетДиагРес** и **СЗЛГетДиагФилд** не публикуют диагностические записи о себе.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Правила диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Роль диспетчера драйверов](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Роль драйвера](../../../odbc/reference/develop-app/role-of-the-driver.md)
