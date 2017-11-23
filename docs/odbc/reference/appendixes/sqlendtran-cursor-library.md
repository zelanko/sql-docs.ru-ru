---
title: "SQLEndTran (библиотека курсоров) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b7ca0f1299933293990fc2c977a4a6602f9d4400
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональность курсора драйвера.  
  
 В этом разделе рассматриваются вопросы применения **SQLEndTran** функции в библиотеку курсоров. Общие сведения о **SQLEndTran**, в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 Библиотека курсоров, не поддерживает транзакции и передает вызовы **SQLEndTran** непосредственно к драйверу. Тем не менее библиотеку курсоров поддерживает фиксации и отката курсора, возвращаемых источником данных с типами сведения SQL_CURSOR_ROLLBACK_BEHAVIOR и SQL_CURSOR_COMMIT_BEHAVIOR:  
  
-   Для источников данных, которые сохраняют курсоры в транзакции изменения которых выполняется откат в источнике данных не откатываются в кэше библиотеку курсоров. Чтобы кэша, которые соответствуют данным в источнике данных, приложение необходимо закрыть и заново откройте курсор.  
  
-   Для источников данных, в которых закрытие курсоров на границы транзакций библиотеку курсоров закрывает курсоры и удаляет кэши для всех инструкций в соединении.  
  
-   Для источников данных, удаление подготовленных инструкций на границы транзакций приложение должно reprepare всех подготовленных инструкций в соединении, прежде чем выполнить их повторно.
