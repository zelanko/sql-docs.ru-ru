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
ms.openlocfilehash: 7184c8ac9e0ad1813999a276f1579351f98544ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020397"
---
# <a name="role-of-the-driver-manager"></a>Роль диспетчера драйверов
Диспетчер драйверов определяет окончательный порядок, в котором возвращаются генерируемые записи о состоянии. В частности, он определяет, какая запись имеет наивысший ранг и должна возвращаться первыми. Драйвер отвечает за упорядочение создаваемых записей о состоянии. Если записи о состоянии публикуются как диспетчер драйверов, так и драйвер, диспетчер драйверов отвечает за их упорядочивание. Дополнительные сведения см. в разделе [последовательность записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Диспетчер драйверов выполняет как можно больше проверок на наличие ошибок. Это позволяет экономить все драйверы от проверки на наличие тех же ошибок. Например, если аргумент функции принимает дискретное число значений, например *операцию* в **SQLSetPos**, диспетчер драйверов проверяет, является ли указанное значение допустимым.  
  
 В следующих разделах описываются типы условий, проверяемые диспетчером драйверов. Они не должны быть исчерпывающими; полный список SQLSTATE, возвращаемых диспетчером драйверов, см. в разделе "Диагностика" каждой функции. Описание каждой проверки, выполненной диспетчером драйверов, начинается с букв «(DM)». См. также таблицы переходов состояния в [приложении б: таблицы перехода состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md). ошибки, показанные в круглых скобках, обнаруживаются диспетчером драйверов.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Проверки значения аргумента](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Проверки переходов состояний](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Проверка общих ошибок](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Проверка ошибок и предупреждений диспетчера драйверов](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
