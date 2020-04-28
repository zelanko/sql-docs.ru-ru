---
title: Освобождение обработчика инструкций ODBC | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01e4cb46edf1b1a0f1c6dfaa0273c1dd5b392686
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305619"
---
# <a name="freeing-a-statement-handle-odbc"></a>Освобождение дескриптора инструкции (ODBC)
Как упоминалось ранее, более эффективно использовать инструкции, чем удалять их и выделять новые. Перед выполнением новой инструкции SQL в инструкции приложения должны быть уверены в том, что параметры текущей инструкции подходят. в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, параметры и результирующие наборы для старой инструкции SQL должны быть несвязанными (путем вызова **SQLFreeStmt** с параметрами SQL_RESET_PARAMS и SQL_UNBIND) и повторной привязки для новой инструкции SQL.  
  
 Когда приложение завершит работу с инструкцией, оно вызывает **SQLFreeHandle** , чтобы освободить инструкцию. После освобождения инструкции возникает ошибка программирования приложения для использования обработчика инструкции в вызове функции ODBC. Это не определено, но, возможно, некритические последствия.  
  
 При вызове **SQLFreeHandle** драйвер освобождает структуру, используемую для хранения сведений об инструкции.  
  
 **SQLDisconnect** автоматически освобождает все инструкции по подключению.
