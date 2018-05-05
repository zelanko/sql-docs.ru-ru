---
title: Тестирование соединения ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 71dbb7da6b52d8715068b270dee6a85ab564e0e6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="testing-the-odbc-connection"></a>Тестирование соединения ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 При устранении неполадок ODBC доступа к базе данных Oracle 7.x и РСУБД Oracle8 серверов, он может потребоваться убедитесь, что базовый SQL * Net и адаптеры протокола Oracle установлены правильно. Чтобы сделать это, программа Oracle предоставленный Nettest.exe в каталоге Orawin\Bin.  
  
 Nettest — это простая программа, которая пытается войти в систему на выбранном сервере, используя только установленного SQL * Net программное обеспечение, которое входит в состав клиента Oracle. Программа запросит имя входа, пароль и TNS строка подключения. Если клиент Oracle установлен правильно, программа выведет просто «Ping успешно». Если имя входа не была успешной, необходимо проконсультироваться с администратором базы данных.
