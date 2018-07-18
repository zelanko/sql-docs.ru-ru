---
title: Быстрые однопроходные курсоры (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e0770356739a1f6c4587f7ce77dccfe3a7bc4d1a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412094"
---
# <a name="fast-forward-only-cursors-odbc"></a>Быстрые курсоры последовательного доступа (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает способы оптимизации производительности однопроходный, только для чтения курсоры. Быстрые однопроходные курсоры реализуются драйвером и сервером внутренне, при этом способ реализации очень похож на результирующие наборы по умолчанию. Кроме того, имея высокую производительность, быстрые однопроходные курсоры обладают следующими характеристиками.  
  
-   [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) не поддерживается. Столбцы результирующего набора должны быть привязаны к переменным программы.  
  
-   Когда сервер достигает конца курсора, он автоматически закрывает курсор. Приложение по-прежнему необходимо вызвать [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) или [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), но драйвер не нужно отправить запрос на закрытие на сервер. Это экономит обращение через сеть к серверу.  
  
 Приложение запрашивает быстрые однопроходные курсоры при помощи атрибута инструкции SQL_SOPT_SS_CURSOR_OPTIONS, зависящего от драйвера. При установке значения SQL_CO_FFO быстрые однопроходные курсоры разрешаются без автоматической выборки. При установке значения SQL_CO_FFO_AF включен параметр автоматической выборки. Дополнительные сведения об автоматической выборке см. в разделе [использование автоматической выборки с помощью курсоров ODBC](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md).  
  
 Быстрые однопроходные курсоры с автоматической выборкой можно использовать для получения небольшого результирующего набора с однократным обращением к серверу. На этих шагах *n* число возвращаемых строк:  
  
1.  Установите для атрибута SQL_SOPT_SS_CURSOR_OPTIONS значение SQL_CO_FFO_AF.  
  
2.  Значение атрибута SQL_ATTR_ROW_ARRAY_SIZE *n* + 1.  
  
3.  Свяжите столбцы результата к массивам *n* + 1 элементов (чтобы обезопасить себя Если *n* + фактически извлеченных строк: 1).  
  
4.  Откройте курсор при помощи либо **SQLExecDirect** или **SQLExecute**.  
  
5.  Если возвращаемое состояние SQL_SUCCESS, затем вызвать **SQLFreeStmt** или **SQLCloseCursor** для закрытия курсора. Все данные для строк будут находиться в связанных программных переменных.  
  
 Таким образом **SQLExecDirect** или **SQLExecute** отправляет запрос на открытие курсора с включенным параметром автоматической выборки. В ответ на этот отдельный запрос от клиента сервер:  
  
-   Открывает курсор.  
  
-   Строит результирующий набор и отправляет строки клиенту.  
  
-   Так как размер набора строк был установлен в значение на 1 большее, чем число строк результирующего набора, сервер определяет конец курсора и закрывает его.  
  
## <a name="see-also"></a>См. также  
 [Подробные сведения о программировании курсоров &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
