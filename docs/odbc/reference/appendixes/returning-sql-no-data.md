---
title: Возвращающиеся SQL_NO_DATA Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e2c806edd5d5647e09c00975ad7207ee5c2c876
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305115"
---
# <a name="returning-sql_no_data"></a>Возврат SQL_NO_DATA
Когда приложение ODBC *2.x,* работая с драйвером ODBC *3.x,* вызывает **s'LExecDirect,** **S'L-Выполняете**, или **S'LParamData**, и выполняется поисковое обновление или удаление оператора, но не влияет на любые строки в источнике данных, водитель ODBC *3.x* должен вернуться SQL_SUCCESS. Когда приложение ODBC *3.x,* работая с драйвером ODBC *3.x,* вызывает **s'LExecDirect,** **S'L-Исполнителе**или **S'LParamData** с тем же результатом, водитель ODBC *3.x* должен вернуться SQL_NO_DATA.  
  
 Если поисковое обновление или удаление оператора в пакете выписок не влияет на какие-либо строки в источнике данных, SQL_SUCCESS возвращается **s'LMoreResults.** Он не может вернуть SQL_NO_DATA, потому что это будет означать, что нет больше результатов, а не что есть результат от поиска обновления / удаления, которые не затрагивают строки.
