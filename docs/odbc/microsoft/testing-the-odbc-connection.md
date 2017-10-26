---
title: "Тестирование соединения ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6875fa4ac03511b57239deadac748da1c37a0114
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="testing-the-odbc-connection"></a>Тестирование соединения ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 При устранении неполадок ODBC доступа к базе данных Oracle 7.x и РСУБД Oracle8 серверов, он может потребоваться убедитесь, что базовый SQL * Net и адаптеры протокола Oracle установлены правильно. Чтобы сделать это, программа Oracle предоставленный Nettest.exe в каталоге Orawin\Bin.  
  
 Nettest — это простая программа, которая пытается войти в систему на выбранном сервере, используя только установленного SQL * Net программное обеспечение, которое входит в состав клиента Oracle. Программа запросит имя входа, пароль и TNS строка подключения. Если клиент Oracle установлен правильно, программа выведет просто «Ping успешно». Если имя входа не была успешной, необходимо проконсультироваться с администратором базы данных.

