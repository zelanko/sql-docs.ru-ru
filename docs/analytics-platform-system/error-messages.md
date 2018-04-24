---
title: Сообщения об ошибках - Parallel Data Warehouse | Документы Microsoft
description: Параллельные хранилища данных (PDW) ошибок регистрации ошибок и проблем, обнаруженных компонентов PDW и может также включать ошибок SQL Server в PDW. Эти сообщения об ошибках использовать единый синтаксис для предоставления сведений. Основные сведения о этот синтаксис дает возможность определять и устранять неполадки.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 33bdf11388ae52959d264e2df091e9c9669b159b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Сообщения об ошибках в Parallel Data Warehouse

Параллельные хранилища данных (PDW) ошибок регистрации ошибок и проблем, обнаруженных компонентов PDW и может также включать ошибок SQL Server в PDW. Эти сообщения об ошибках использовать единый синтаксис для предоставления сведений. Основные сведения о этот синтаксис дает возможность обнаружения и устранения неполадок в SQL Server PDW.  
  
## <a name="Basics"></a>Основы сообщений ошибки  
Сообщения об ошибках, возвращаемых имеют одинаковый синтаксис.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Это потенциальные значения для каждого поля.  
  
|Поле|Описание|Пример|  
|---------|---------------|-----------|  
|*Error_Indicator*|Слово «Ошибка» или другой текст, предупреждающее, что для устранения ошибки.|ERROR|  
|*SQL_State_Code*|Код состояния SQL в соответствии со спецификацией ODBC. Драйвер создает соответствующий код состояния SQL каждый раз, когда он возвращает сообщение в приложение. Текст «Microsoft» указывает источник ошибки.|42000|  
|*Driver_Details*|Сведения, зависящие от драйвера, как тип драйвера, используемого.|Драйвер ODBC SQL Server 2008 R2 параллельного хранилища данных|  
|*QueryID*|Уникальный идентификатор для запроса. Это значение можно используйте для поиска дополнительных сведений, относящихся к обработке запроса. Например сведения о выполнении запроса можно найти в консоли администрирования с помощью ИД запроса. Дополнительные сведения см. в разделе [отслеживать устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Если QueryID неприменим, пользователю возвращается текст «Internal».|QID2377|  
|*Message_String*|Понятное описание ошибки или проблемы. При возврате ошибок SQL Server, это текст сообщения SQL Server.|Только равные назначения могут отображаться в списке set инструкции UPDATE.|  
  
Эти примеры значений будут представлены пользователю следующим образом:  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Основные сведения об оповещениях в консоли администрирования](understanding-admin-console-alerts.md)  
  
