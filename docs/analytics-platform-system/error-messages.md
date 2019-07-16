---
title: Сообщения об ошибках - Parallel Data Warehouse | Документация Майкрософт
description: Parallel Data Warehouse (PDW) ошибок регистрации ошибок и проблем, обнаруженных компонентов PDW, а также может содержать ошибки SQL Server, доступных через PDW. Эти сообщения об ошибках используйте единым синтаксисом для представления информации. Основные сведения об этом синтаксисе позволит вам выявлять и устранять неполадки.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 78c5cd8dab37ac9cb32de794861c68e6c8085747
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960962"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Сообщения об ошибках в Parallel Data Warehouse

Parallel Data Warehouse (PDW) ошибок регистрации ошибок и проблем, обнаруженных компонентов PDW, а также может содержать ошибки SQL Server, доступных через PDW. Эти сообщения об ошибках используйте единым синтаксисом для представления информации. Основные сведения об этом синтаксисе позволит вам выявлять и устранять неполадки в SQL Server PDW.  
  
## <a name="Basics"></a>Основы сообщений ошибки  
Сообщения об ошибках, возвращаемых имеют одинаковый синтаксис.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Ниже приведены возможные значения для каждого поля.  
  
|Поле|Описание|Пример|  
|---------|---------------|-----------|  
|*Error_Indicator*|Слово «Ошибка» или другой текст, предупреждающее, что для устранения ошибки.|ошибка|  
|*SQL_State_Code*|Код состояния SQL в соответствии со спецификацией ODBC. Драйвер создает соответствующий код состояния SQL каждый раз, когда он возвращает сообщение в приложение. Текст «Microsoft» указывает на источник ошибки.|42000|  
|*Driver_Details*|Сведения, зависящие от драйвера, как тип драйвера, используемого.|Драйвер ODBC SQL Server 2008 R2 Parallel Data Warehouse|  
|*QueryID*|Уникальный идентификатор для запроса. Используйте это значение для поиска дополнительных сведений, связанных с обработкой запроса. Например сведения о выполнении запроса можно найти в консоли администрирования с помощью идентификатора запроса. Дополнительные сведения см. в разделе [мониторинг устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Если QueryID неприменим, «Внутреннее» возвращается пользователю.|QID2377|  
|*Message_String*|Понятное описание ошибки или проблемы. При возвращении ошибок SQL Server, это текст сообщения SQL Server.|Только равные назначения могут отображаться в списке set инструкции UPDATE.|  
  
Эти примеры значений будет доступен для пользователя следующим образом:  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Основные сведения о предупреждениях консоли администрирования](understanding-admin-console-alerts.md)  
  
