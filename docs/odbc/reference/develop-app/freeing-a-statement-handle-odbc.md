---
title: Освобождение дескриптора инструкции ODBC | Документы Microsoft
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
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c0b56bfd04724c8506b5ba0fe7b5fd01a57a02e7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="freeing-a-statement-handle-odbc"></a>Освобождение дескриптора инструкции ODBC
Как упоминалось ранее, более эффективна для повторного использования инструкций, чем их удаление и повторное выделение. Перед выполнением новой инструкции SQL на инструкции, приложения должны быть в том, что подходят текущих параметров инструкции. в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, параметров и результирующих наборов для старой инструкции SQL должны быть свободной (путем вызова **SQLFreeStmt** с параметрами SQL_RESET_PARAMS и SQL_UNBIND) и восстановления для новой инструкции SQL.  
  
 Когда приложение завершило инструкцией, он вызывает **SQLFreeHandle** освободить инструкцию. После освобождения инструкцию, это ошибка программирования приложения для использования дескриптора инструкции в вызове функции ODBC; Таким образом, это должна не определено, но, возможно, Неустранимая последствия.  
  
 Когда **SQLFreeHandle** вызывается версиях драйвера, структура, используемая для хранения сведений об инструкции.  
  
 **SQLDisconnect** автоматически освобождает все инструкции для подключения.
