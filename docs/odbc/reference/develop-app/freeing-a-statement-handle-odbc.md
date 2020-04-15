---
title: Освобождение заявление Ручка ODBC (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305619"
---
# <a name="freeing-a-statement-handle-odbc"></a>Освобождение дескриптора инструкции (ODBC)
Как упоминалось ранее, более эффективно повторно использовать заявления, чем отбросить их и выделить новые. Перед выполнением новой выписки по заявлению s'L приложения должны быть уверены в том, что текущие настройки оператора являются подходящими. в частности атрибуты инструкции, привязки параметров и привязки результирующего набора. Как правило, параметры и наборы результатов для старого оператора S'L должны быть несвязанными (позвонив в **S-LFreeStmt** с SQL_RESET_PARAMS и SQL_UNBIND опций) и отскочить для нового оператора S'L.  
  
 Когда приложение закончило использовать выписку, оно вызывает **S'LFreeHandle,** чтобы освободить выписку. После освобождения оператора использование ошибки программирования приложения — это ошибка программирования приложения при вызове к функции ODBC; это имеет неопределенные, но, вероятно, фатальные последствия.  
  
 При вызове **S'LFreeHandle** драйвер выпускает структуру, используемую для хранения информации об этом заявлении.  
  
 **S'LDisconnect** автоматически освобождает все операторы на подключение.
