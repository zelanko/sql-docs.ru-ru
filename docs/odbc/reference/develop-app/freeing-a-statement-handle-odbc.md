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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 638cf9fb3c7af73130cf1413559b9baee2a354c1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069781"
---
# <a name="freeing-a-statement-handle-odbc"></a>Освобождение дескриптора инструкции (ODBC)
Как упоминалось ранее, более эффективно использовать инструкции, чем удалять их и выделять новые. Перед выполнением новой инструкции SQL в инструкции приложения должны быть уверены в том, что параметры текущей инструкции подходят. в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, параметры и результирующие наборы для старой инструкции SQL должны быть несвязанными (путем вызова **SQLFreeStmt** с параметрами SQL_RESET_PARAMS и SQL_UNBIND) и повторной привязки для новой инструкции SQL.  
  
 Когда приложение завершит работу с инструкцией, оно вызывает **SQLFreeHandle** , чтобы освободить инструкцию. После освобождения инструкции возникает ошибка программирования приложения для использования обработчика инструкции в вызове функции ODBC. Это не определено, но, возможно, некритические последствия.  
  
 При вызове **SQLFreeHandle** драйвер освобождает структуру, используемую для хранения сведений об инструкции.  
  
 **SQLDisconnect** автоматически освобождает все инструкции по подключению.
