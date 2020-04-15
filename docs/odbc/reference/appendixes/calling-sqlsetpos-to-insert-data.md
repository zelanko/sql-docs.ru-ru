---
title: Вызов S'LSetPos для вставки данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb374b2506d55b400207c8f60bdf42bb6bb4065e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306605"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>Вызов SQLSetPos для вставки данных
Когда приложение ODBC *2.x,* работая с драйвером ODBC *3.x,* вызывает **S'LSetPos** с *аргументом операции* SQL_ADD, менеджер драйвера не отображает этот вызов в **S'LBulkOperations.** Если водитель ODBC *3.x* должен работать с приложением, которое вызывает **S'LSetPos** с SQL_ADD, водитель должен поддерживать эту операцию.  
  
 Одно из основных различий в поведении, когда **S'LSetPos** называется с SQL_ADD происходит, когда он называется в состоянии S6. В ODBC *2.x*, водитель вернулся S1010, когда **S'LSetPos** был вызван с SQL_ADD в состоянии S6 (после курсор был расположен с **S'LFetch**). В ODBC *3.x*, **S'LBulkOperations** с *операцией* SQL_ADD можно вызвать в состоянии S6. Второе существенное отличие в поведении заключается в том, что **s'LBulkOperations** с *операцией* SQL_ADD может быть вызван в состоянии S5, в то время как **S'LSetPos** с **операцией** SQL_ADD не может. Для переходов оператора, которые могут возникнуть для одного и [Appendix B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)того же вызова в ODBC *3.x,* см.
