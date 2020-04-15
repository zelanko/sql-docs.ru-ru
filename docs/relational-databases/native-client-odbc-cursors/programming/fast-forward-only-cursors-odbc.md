---
title: Перемотка вперед-только курсоры (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 50d79875e0f3f661c0a959f50ce68c4f2761d186
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298424"
---
# <a name="fast-forward-only-cursors-odbc"></a>Быстрые курсоры последовательного доступа (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  При подключении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляру драйвер ODBC Native Client поддерживает оптимизацию производительности для курсоров только для чтения. Быстрые однопроходные курсоры реализуются драйвером и сервером внутренне, при этом способ реализации очень похож на результирующие наборы по умолчанию. Кроме того, имея высокую производительность, быстрые однопроходные курсоры обладают следующими характеристиками.  
  
-   [S'LGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) не поддерживается. Столбцы результирующего набора должны быть привязаны к переменным программы.  
  
-   Когда сервер достигает конца курсора, он автоматически закрывает курсор. Приложение по-прежнему должно вызывать [s'LCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) или [S'LFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), но водитель не должен отправлять близкий запрос на сервер. Это экономит обращение через сеть к серверу.  
  
 Приложение запрашивает быстрые однопроходные курсоры при помощи атрибута инструкции SQL_SOPT_SS_CURSOR_OPTIONS, зависящего от драйвера. При установке значения SQL_CO_FFO быстрые однопроходные курсоры разрешаются без автоматической выборки. При установке значения SQL_CO_FFO_AF включен параметр автоматической выборки. Для получения дополнительной информации о autofetch, [см.](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md)  
  
 Быстрые однопроходные курсоры с автоматической выборкой можно использовать для получения небольшого результирующего набора с однократным обращением к серверу. В этих шагах *n* — это количество строк, которые будут возвращены:  
  
1.  Установите для атрибута SQL_SOPT_SS_CURSOR_OPTIONS значение SQL_CO_FFO_AF.  
  
2.  Установить SQL_ATTR_ROW_ARRAY_SIZE *n* No 1.  
  
3.  Привязать столбцы результатов к массивам *элементов n* no 1 (чтобы быть безопасным, если *n* q 1 строки на самом деле извлечены).  
  
4.  Откройте курсор с **помощью s'LExecDirect** или **S'LExecute.**  
  
5.  Если статус возврата SQL_SUCCESS, позвоните по телефону **s'LFreeStmt** или **S'LCloseCursor,** чтобы закрыть курсор. Все данные для строк будут находиться в связанных программных переменных.  
  
 С помощью этих шагов, **S'LExecDirect** или **S'LExecute** отправляет запрос на открытый курсор с включенной опцией autofetch. В ответ на этот отдельный запрос от клиента сервер:  
  
-   Открывает курсор.  
  
-   Строит результирующий набор и отправляет строки клиенту.  
  
-   Так как размер набора строк был установлен в значение на 1 большее, чем число строк результирующего набора, сервер определяет конец курсора и закрывает его.  
  
## <a name="see-also"></a>См. также:  
 [Курзор Программирование Подробности &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
