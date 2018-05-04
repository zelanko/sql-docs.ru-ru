---
title: Роли диспетчера драйверов | Документы Microsoft
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
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 525c29976ac596338fd18a84a5ab5f143eca7632
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="role-of-the-driver-manager"></a>Роли диспетчера драйверов
Диспетчер драйверов определяет окончательный порядок, в котором для возвращения состояния записи, которые создает. В частности он определяет, какая запись имеет наивысший ранг и возвращается сначала. Драйвер отвечает за упорядочения записей состояния, которые он создает. Если записи состояния учитываются, диспетчер драйверов и драйвер, диспетчер драйверов отвечает за их упорядочивание. Дополнительные сведения см. в разделе [последовательности записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Диспетчер драйверов выполняет столько проверку ошибок, как. Это экономит драйверах проверки наличия те же ошибки. Например, если аргумент функции принимает ряд дискретных значений, таких как *операции* в **SQLSetPos**, диспетчер драйверов проверяет, что указанное значение является допустимым.  
  
 В следующих разделах описаны типы условий, проверяется с помощью диспетчера драйверов. Они не предназначены для исчерпывающим; Полный список SQLSTATE возвращает диспетчера драйверов, см. в разделе «Диагностика» каждой функции; Описание каждого проверка диспетчером драйверов начинается с букв «(DM)». См. также таблицы перехода состояний в [приложение б: ODBC состояния перехода таблиц](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); диспетчером драйверов обнаружены ошибки, показывается в скобках.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Проверки значения аргумента](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Проверки переходов состояний](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Проверка общих ошибок](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Проверка ошибок и предупреждений диспетчера драйверов](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
