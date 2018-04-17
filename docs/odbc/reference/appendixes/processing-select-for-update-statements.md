---
title: Обработка SELECT для инструкций UPDATE | Документы Microsoft
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
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c1af5a6c3bdd4a04f0d901158643e29d40962a6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="processing-select-for-update-statements"></a>Обработка SELECT для инструкции UPDATE
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 Для максимальной совместимости приложений должна создавать результирующие наборы, которые будут обновлены с помощью инструкции позиционированного обновления, выполнив **ВЫБЕРИТЕ для обновления** инструкции. Несмотря на то, что библиотека курсоров это не требуется, она затребована большинство источников данных, поддерживающих инструкции позиционированного обновления.  
  
 Библиотека курсоров не учитывает столбцы в **FOR UPDATE** предложения **SELECT FOR UPDATE** инструкции; прежде чем передавать инструкции драйвер удаляет это предложение. В библиотеку курсоров атрибут инструкции SQL_ATTR_CONCURRENCY, а также ограничения, упомянутых в предыдущем разделе, элементы управления ли столбцы из результирующего набора могут обновляться.
