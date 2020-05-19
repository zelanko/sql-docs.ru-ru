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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4e8bcae5ab64fff47528c30a67c13fd1c859ea4e
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702032"
---
# <a name="using-server-cursors"></a>Использование серверных курсоров
  Если приложение ODBC устанавливает для любого из атрибутов курсора ODBC значение, отличное от значений по умолчанию, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента запрашивает сервер для реализации серверного курсора API того же типа. Использование серверных курсоров API-интерфейса обеспечивает высвобождение памяти клиента и может существенно сократить объем сетевого трафика между клиентом и сервером.  
  
 Возможным недостатком серверных курсоров API является то, что они в настоящее время поддерживают не все инструкции SQL. Серверные курсоры API-интерфейса не могут быть использованы для выполнения следующих задач:  
  
-   пакеты или хранимые процедуры, которые возвращают несколько результирующих наборов;  
  
-   инструкции SELECT, которые содержат предложения COMPUTE, COMPUTE BY, FOR BROWSE или INTO;  
  
-   инструкцию EXECUTE, которая содержит ссылку на удаленную хранимую процедуру.  
  
 При подключении к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполнение инструкции с данными характеристиками с помощью серверного курсора приводит к тому, что курсор преобразуется в принимаемый по умолчанию результирующий набор. При подключении к более ранним версиям [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возникает ошибка.  
  
## <a name="see-also"></a>См. также  
 [Способы реализации курсоров](how-cursors-are-implemented.md)  
  
  
