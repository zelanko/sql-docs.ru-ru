---
title: Граница vs. Отсутствует привязка столбцами Text и Image | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c5129c6b865723721bbb6f176893c950cdf905fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097045"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Граница vs. Несвязанный текст и столбцы изображений
  При использовании серверных курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента оптимизируется для запрещения передачи данных непривязанным **текст**, **ntext**, или **изображения** столбцы в время **SQLFetch** выполняется. **Текст**, **ntext**, или **изображения** данных не производится на сервере до проблемы с приложением [SQLGetData](../native-client-odbc-api/sqlgetdata.md) для столбец.  
  
 Многие приложения могут быть написаны таким образом, что не **текст**, **ntext**, или **изображения** данные отображаются при прокрутке пользователем вверх и вниз в курсоре. Когда пользователь выбирает строку, чтобы получить более подробные сведения, приложение может затем вызвать **SQLGetData** для получения **текст**, **ntext**, или **изображения** данные. Это предотвратит передачу **текст**, **ntext**, или **изображения** данные для строк, пользователь не выбрать и таким образом запретит передачу очень большой объемы данных.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами Text и Image](managing-text-and-image-columns.md)   
 [Режимы работы курсоров](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  