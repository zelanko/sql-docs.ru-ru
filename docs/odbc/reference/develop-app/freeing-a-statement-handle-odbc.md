---
title: Освобождение дескриптора инструкции ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc16e820671aa69c15365413d44fb9bcf807236b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757732"
---
# <a name="freeing-a-statement-handle-odbc"></a>Освобождение дескриптора инструкции (ODBC)
Как упоминалось ранее, более эффективным будет повторное использование инструкций, чем их удаление и выделение. Перед выполнением новой инструкции SQL на инструкции, приложений, следует убедиться, что что текущих параметров инструкции подходят. в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, требуется параметров и результирующих наборов для старой инструкции SQL отменяется привязка (путем вызова **SQLFreeStmt** с параметрами SQL_RESET_PARAMS и SQL_UNBIND) и восстановления для новой инструкции SQL.  
  
 Когда приложение завершило с помощью инструкции, он вызывает **SQLFreeHandle** чтобы освободить ее. После освобождения инструкцию, это приложение, ошибка программирования для использования дескриптора инструкции в вызове функции ODBC; имеет неопределенный, но, возможно, Неустранимая последствия.  
  
 Когда **SQLFreeHandle** вызывается освобождает драйвера, структуры, используемые для хранения сведений об инструкции.  
  
 **SQLDisconnect** автоматически освобождает все инструкции для подключения.
