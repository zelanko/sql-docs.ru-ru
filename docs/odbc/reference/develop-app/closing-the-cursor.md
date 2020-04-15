---
title: Закрытие Курсора Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 723e40e6d83eed84ed93ee1eeab3535622ad5f04
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299144"
---
# <a name="closing-the-cursor"></a>Закрытие курсора
Когда приложение закончило с помощью курсора, оно вызывает **S'LCloseCursor,** чтобы закрыть курсор. Пример:  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 До тех пор, пока приложение не закроет курсор, заявление, на котором открывается курсор, не может быть использовано для большинства других операций, таких как выполнение другого оператора S'L. Полный список функций, которые можно вызвать во [Appendix B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)время открытия курсора, см.  
  
> [!NOTE]  
>  Чтобы закрыть курсор, приложение должно позвонить в **s'LCloseCursor,** а не на **S'LCancel.**  
  
 Курсоры остаются открытыми до тех пор, пока они явно не будут закрыты, за исключением случаев, когда транзакция зафиксирована или отката, и в этом случае некоторые источники данных закрывают курсор. В частности, достижение конца набора результатов, когда **s'LFetch** возвращается SQL_NO_DATA, не закрывает курсор. Даже курсоры на пустых наборах результатов (наборы результатов, созданные при успешном выполнении оператора, но не возвратившее строки) должны быть явно закрыты.
