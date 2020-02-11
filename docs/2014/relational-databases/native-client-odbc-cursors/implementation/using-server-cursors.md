---
title: Использование серверных курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: cef56db912d786b6908271d0747fe45690e90536
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63011843"
---
# <a name="using-server-cursors"></a>Использование серверных курсоров
  Если приложение ODBC устанавливает для любого из атрибутов курсора ODBC значение, отличное от значений по умолчанию, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента запрашивает сервер для реализации серверного КУРСОРа API того же типа. Использование серверных курсоров API-интерфейса обеспечивает высвобождение памяти клиента и может существенно сократить объем сетевого трафика между клиентом и сервером.  
  
 Возможным недостатком серверных курсоров API является то, что они в настоящее время поддерживают не все инструкции SQL. Серверные курсоры API-интерфейса не могут быть использованы для выполнения следующих задач:  
  
-   пакеты или хранимые процедуры, которые возвращают несколько результирующих наборов;  
  
-   инструкции SELECT, которые содержат предложения COMPUTE, COMPUTE BY, FOR BROWSE или INTO;  
  
-   инструкцию EXECUTE, которая содержит ссылку на удаленную хранимую процедуру.  
  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполнение инструкции с данными характеристиками с помощью серверного курсора приводит к тому, что курсор преобразуется в принимаемый по умолчанию результирующий набор. При подключении к более ранним версиям [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возникает ошибка.  
  
## <a name="see-also"></a>См. также:  
 [Способы реализации курсоров](how-cursors-are-implemented.md)  
  
  
