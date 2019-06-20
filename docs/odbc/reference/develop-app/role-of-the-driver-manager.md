---
title: Роль диспетчера драйверов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- diagnostic information [ODBC], driver manager error checking
- SQLGetDiagField function [ODBC], driver manager
- SQLGetDiagRec function [ODBC], driver manager
- ODBC driver manager [ODBC]
- diagnostic information [ODBC], SqlGetDiagRec
- driver manager [ODBC], error checking
ms.assetid: 7b861c82-357e-4590-8074-45136e9ed15e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 485cd951992ed427461e497c53d17a4f6db24a38
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127239"
---
# <a name="role-of-the-driver-manager"></a>Роль диспетчера драйверов
Диспетчер драйверов определяет конечного порядка, в которую будет возвращен записи состояния, которые она создает. В частности он определяет, какая запись с наивысшим рангом и возвращается сначала. Драйвер несет ответственность за упорядочение записи состояния, которые он создает. Если записи состояния учитываются, диспетчер драйверов и драйвер, диспетчер драйверов несет ответственность за их упорядочивание. Дополнительные сведения см. в разделе [последовательность записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Диспетчер драйверов выполняет столько ошибки проверки, как. Это сохраняет каждый драйвер проверять те же ошибки. Например, если аргумент функции принимает ряд дискретных значений, такие как *операции* в **SQLSetPos**, диспетчер драйверов проверяет, что указанное значение является допустимым.  
  
 Типы условий, проверяется диспетчером драйверов в следующих разделах. Они не предназначены для выполнить более тщательную проверку; Полный список SQLSTATE, возвращает диспетчера драйверов см. в разделе «Диагностика» каждой функции; Описание каждой проверки, внесенные диспетчером драйверов начинается с букв «(DM).» Также см. таблицы перехода состояния в [приложении б: Таблицы перехода состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); обнаружено ошибок, показывается в скобках диспетчером драйверов.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Проверки значения аргумента](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Проверки переходов состояний](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Проверка общих ошибок](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Проверка ошибок и предупреждений диспетчера драйверов](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
