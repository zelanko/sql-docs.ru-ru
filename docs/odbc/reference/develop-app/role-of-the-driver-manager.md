---
title: Роль менеджера по драйверам Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee3d704ea43125c3cd912a4e67d90bf5d50c733e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304305"
---
# <a name="role-of-the-driver-manager"></a>Роль диспетчера драйверов
Менеджер драйвера определяет окончательный порядок возврата записей статуса, которые он генерирует. В частности, он определяет, какой рекорд имеет самый высокий ранг и должен быть возвращен первым. Водитель отвечает за заказ записей о состоянии, которые он генерирует. Если записи о состоянии публикуются как менеджером водителя, так и водителем, менеджер драйвера несет ответственность за их заказ. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
 Менеджер драйвера делает столько ошибок проверки, как это может. Это избавит каждого водителя от проверки на наличие одних и тех же ошибок. Например, если аргумент функции принимает дискретное число значений, таких как *операция* в **S'LSetPos,** менеджер драйвера проверяет, что указанное значение является законным.  
  
 В следующих разделах описаны типы условий, проверенных менеджером драйвера. Они не должны быть исчерпывающими; для получения полного перечня S'LSTATEs, который возвращает менеджер драйвера, см. описание каждой проверки, сделанной менеджером драйвера, начинается с букв "(DM)". Также смотрите таблицы перехода состояния в [приложении B: Таблицы перехода состояния ODBC;](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md) ошибки, указанные в скобках, обнаруживаются менеджером драйверов.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Проверки значения аргумента](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Проверки переходов состояний](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Проверка общих ошибок](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Проверка ошибок и предупреждений диспетчера драйверов](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
