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
ms.openlocfilehash: 02509ddb6a986ebb7796d80aca10c6f18cde6e69
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67939709"
---
# <a name="testing-the-odbc-connection"></a>Тестирование подключения ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 При устранении неполадок доступа ODBC к серверам Oracle 7. x и Oracle8 РСУБД может потребоваться проверить правильность установки базовых адаптеров протокола SQL * NET и Oracle. Для этого используйте программу Неттест. exe, предоставляемую Oracle, в каталоге Оравин\бин.  
  
 Неттест — это простая программа, которая пытается войти на выбранный сервер, используя только установленное программное обеспечение SQL * NET, которое является частью клиента Oracle. Программа запросит имя входа, пароль и строку подключения TNS. Если клиент Oracle установлен правильно, программа просто выведет сообщение PING успешно. Если имя входа не прошло успешно, необходимо обратиться к администратору базы данных.
