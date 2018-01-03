---
title: "Сообщения об ошибках (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6223cba-2dec-4b8a-bc10-e2ef6a821fe0
caps.latest.revision: "9"
ms.openlocfilehash: c9c0ebf9b452fdf2ec54ae84bec34288e73e88aa
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="error-messages"></a>сообщения об ошибках
Сообщения об ошибках SQL Server PDW регистрации ошибок и проблем, обнаруженных компонентов SQL Server PDW, а также может содержать ошибки SQL Server в SQL Server PDW. Эти сообщения об ошибках использовать единый синтаксис для предоставления сведений. Основные сведения о этот синтаксис дает возможность обнаружения и устранения неполадок в SQL Server PDW.  
  
## <a name="Basics"></a>Основы сообщений ошибки  
Сообщения об ошибках, возвращаемых имеют одинаковый синтаксис.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Это потенциальные значения для каждого поля.  
  
|Поле|Description|Пример|  
|---------|---------------|-----------|  
|*Error_Indicator*|Слово «Ошибка» или другой текст, предупреждающее, что для устранения ошибки.|Ошибка|  
|*SQL_State_Code*|Код состояния SQL в соответствии со спецификацией ODBC. Драйвер создает соответствующий код состояния SQL каждый раз, когда он возвращает сообщение в приложение. Текст «Microsoft» указывает источник ошибки.|42000|  
|*Driver_Details*|Сведения, зависящие от драйвера, как тип драйвера, используемого.|Драйвер ODBC SQL Server 2008 R2 параллельного хранилища данных|  
|*QueryID*|Уникальный идентификатор для запроса. Это значение можно используйте для поиска дополнительных сведений, относящихся к обработке запроса. Например сведения о выполнении запроса можно найти в консоли администрирования с помощью ИД запроса. Дополнительные сведения см. в разделе [отслеживать устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Если QueryID неприменим, пользователю возвращается текст «Internal».|QID2377|  
|*Message_String*|Понятное описание ошибки или проблемы. При возврате ошибок SQL Server, это текст сообщения SQL Server.|Только равные назначения могут отображаться в списке set инструкции UPDATE.|  
  
Эти примеры значений будут представлены пользователю следующим образом:  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>См. также:  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Основные сведения об оповещениях в консоли администрирования](understanding-admin-console-alerts.md)  
  
