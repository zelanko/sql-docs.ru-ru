---
title: Использование серверных курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74107cf78427efca5042edbf10e3e0991ec47b8c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134017"
---
# <a name="using-server-cursors"></a>Использование серверных курсоров
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Если приложение ODBC задает атрибуты курсора ODBC значение, отличное от значения по умолчанию, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента запрашивает серверу Применить серверный курсор API того же типа. Использование серверных курсоров API-интерфейса обеспечивает высвобождение памяти клиента и может существенно сократить объем сетевого трафика между клиентом и сервером.  
  
 Возможным недостатком серверных курсоров API является то, что они в настоящее время поддерживают не все инструкции SQL. Серверные курсоры API-интерфейса не могут быть использованы для выполнения следующих задач:  
  
-   пакеты или хранимые процедуры, которые возвращают несколько результирующих наборов;  
  
-   инструкции SELECT, которые содержат предложения COMPUTE, COMPUTE BY, FOR BROWSE или INTO;  
  
-   инструкцию EXECUTE, которая содержит ссылку на удаленную хранимую процедуру.  
  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполнение инструкции с данными характеристиками с помощью серверного курсора приводит к тому, что курсор преобразуется в принимаемый по умолчанию результирующий набор. При подключении к более ранним версиям [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возникает ошибка.  
  
## <a name="see-also"></a>См. также  
 [Способы реализации курсоров](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
