---
title: Однопроходные курсоры (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
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
ms.openlocfilehash: 60c9d9aa68e82d21e2fffed026944e6a04b9b392
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fast-forward-only-cursors-odbc"></a>Быстрые курсоры последовательного доступа (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает способы оптимизации производительности однопроходный, только для чтения курсоры. Быстрые однопроходные курсоры реализуются драйвером и сервером внутренне, при этом способ реализации очень похож на результирующие наборы по умолчанию. Кроме того, имея высокую производительность, быстрые однопроходные курсоры обладают следующими характеристиками.  
  
-   [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) не поддерживается. Столбцы результирующего набора должны быть привязаны к переменным программы.  
  
-   Когда сервер достигает конца курсора, он автоматически закрывает курсор. Приложение по-прежнему необходимо вызвать [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) или [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), но драйвер не должен отправлять закрыть запрос на сервер. Это экономит обращение через сеть к серверу.  
  
 Приложение запрашивает быстрые однопроходные курсоры при помощи атрибута инструкции SQL_SOPT_SS_CURSOR_OPTIONS, зависящего от драйвера. При установке значения SQL_CO_FFO быстрые однопроходные курсоры разрешаются без автоматической выборки. При установке значения SQL_CO_FFO_AF включен параметр автоматической выборки. Дополнительные сведения об автоматической выборке см. в разделе [использование автоматической выборки с курсорами ODBC](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md).  
  
 Быстрые однопроходные курсоры с автоматической выборкой можно использовать для получения небольшого результирующего набора с однократным обращением к серверу. В этом пошаговом руководстве *n* число возвращаемых строк:  
  
1.  Установите для атрибута SQL_SOPT_SS_CURSOR_OPTIONS значение SQL_CO_FFO_AF.  
  
2.  Значение атрибута SQL_ATTR_ROW_ARRAY_SIZE *n* + 1.  
  
3.  Свяжите столбцы результата к массивам *n* + 1 элементов (во избежание неприятностей Если *n* + 1 строк будет фактически выбрана).  
  
4.  Открытие курсора с помощью **SQLExecDirect** или **SQLExecute**.  
  
5.  Если возвращается состояние SQL_SUCCESS, затем вызовите **SQLFreeStmt** или **SQLCloseCursor** для закрытия курсора. Все данные для строк будут находиться в связанных программных переменных.  
  
 В этом пошаговом **SQLExecDirect** или **SQLExecute** отправляет запрос на открытие курсора с включенным параметром автоматической выборки. В ответ на этот отдельный запрос от клиента сервер:  
  
-   Открывает курсор.  
  
-   Строит результирующий набор и отправляет строки клиенту.  
  
-   Так как размер набора строк был установлен в значение на 1 большее, чем число строк результирующего набора, сервер определяет конец курсора и закрывает его.  
  
## <a name="see-also"></a>См. также  
 [Подробные сведения о программировании курсоров &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
