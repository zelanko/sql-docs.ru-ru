---
title: "Отключение от данных источника или драйвер | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disconnecting from driver [ODBC]
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
- connecting to data source [ODBC], disconnecting
- connecting to driver [ODBC], disconnecting
- ODBC drivers [ODBC], disconnecting
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a08f5de9829ee006c51ef6a2e795b44967c43a99
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Отключение от данных источника или драйвер
После завершения использования источника данных приложение вызывает **SQLDisconnect**. **SQLDisconnect** освобождает все инструкции, выделенные при соединении и отсоединяет драйвер от источника данных. Он возвращает ошибку, если транзакция находится в процессе.  
  
 После отсоединения приложение может вызвать **SQLFreeHandle** для освобождения соединения. После освобождения соединения, это ошибка программирования приложения для использования дескриптора соединения в вызове функции ODBC; Таким образом, это должна не определено, но, возможно, Неустранимая последствия. Когда **SQLFreeHandle** вызывается версиях драйвера, структура, используемая для хранения сведений о соединении.  
  
 Также приложение может повторно использовать соединения, чтобы подключиться к другому источнику данных или повторно подключиться к тому же источнику данных. Требуется решение остается подключенным, в отличие от отсоединения и присоединения в более поздней версии, что разработчик приложения должен рассмотреть сравнительную стоимость каждого варианта; соединение с источником данных и подключенном может быть сравнительно много ресурсов, в зависимости от носителя соединения. При принятии правильный баланс, приложение должно также делать предположения о вероятности и время дальнейших операций на том же источнике данных.

