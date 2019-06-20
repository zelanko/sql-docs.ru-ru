---
title: Тестирование подключения ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 543ab436ac7dca5e0d5965220cd90a798afb5ccf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62633179"
---
# <a name="testing-the-odbc-connection"></a>Тестирование подключения ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 При устранении неполадок ODBC доступа к базе данных Oracle 7.x и серверы Oracle8 реляционной СУБД, он может потребоваться убедитесь, что базовый SQL * Net и адаптеров протокола Oracle установлены правильно. Чтобы сделать это, программа предоставляемую Oracle Nettest.exe в каталоге Orawin\Bin.  
  
 Nettest — это простое средство, которое пытается войти в систему на выбранном сервере, с помощью только установленные SQL * Net программное обеспечение, которое входит в состав клиента Oracle. Программа запросит имя входа, пароль и TNS строка подключения. Если клиент Oracle установлен неправильно, программа просто выведет «Ping успешно». Если имя входа не выполнена, необходимо проконсультироваться с администратором базы данных.
