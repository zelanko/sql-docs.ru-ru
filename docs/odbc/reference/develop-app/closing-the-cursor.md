---
title: Закрытие курсора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de22797bdcf4ff526a8c17aee313567da3114b60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036541"
---
# <a name="closing-the-cursor"></a>Закрытие курсора
Когда приложение завершает работу с курсором, оно вызывает **SQLCloseCursor** , чтобы закрыть курсор. Пример:  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 Пока приложение не закроет курсор, инструкция, на которой открыт курсор, не может использоваться для большинства других операций, таких как выполнение другой инструкции SQL. Полный список функций, которые могут вызываться при открытом курсоре, см. в [приложении б: таблицы перехода состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Чтобы закрыть курсор, приложение должно вызвать **SQLCloseCursor**, а не **SQLCancel**.  
  
 Курсоры остаются открытыми до тех пор, пока они не закрыты явным образом, за исключением случаев фиксации или отката транзакции, в этом случае некоторые источники данных закрывают курсор. В частности, достижение конца результирующего набора, когда **SQLFetch** возвращает SQL_NO_DATA, не закрывает курсор. Даже курсоры на пустых результирующих наборах (результирующие наборы, созданные при успешном выполнении инструкции, но не возвращающие строки) должны быть явно закрыты.
