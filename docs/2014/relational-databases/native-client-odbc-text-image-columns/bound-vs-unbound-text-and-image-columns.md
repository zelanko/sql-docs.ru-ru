---
title: Привязанные и Несвязанных столбцами Text и Image | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d77a71aae13c9601acc0ba56146e7882e6ee6e7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430633"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Привязанные и Столбцами несвязанного Text и Image
  При использовании серверных курсоров, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента оптимизирован для запрещения передачи данных непривязанным **текст**, **ntext**, или **образа** на столбцы время **SQLFetch** выполняется. **Текст**, **ntext**, или **изображение** данных не производится на сервере до проблем приложений [SQLGetData](../native-client-odbc-api/sqlgetdata.md) для столбец.  
  
 Многие приложения могут быть написаны таким образом, чтобы не **текст**, **ntext**, или **изображения** данные отображаются при прокрутке пользователем вверх и вниз в курсоре. Когда пользователь выбирает строку, чтобы получить более подробные сведения, приложение может затем вызвать **SQLGetData** извлекаемого **текст**, **ntext**, или **изображение** данные. Это предотвратит передачу **текст**, **ntext**, или **изображения** данные для строк, пользователь не выберите и таким образом запретит передачу очень больших объемы данных.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами Text и Image](managing-text-and-image-columns.md)   
 [Режимы работы курсоров](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
