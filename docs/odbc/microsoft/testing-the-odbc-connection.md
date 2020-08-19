---
description: Тестирование подключения ODBC
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61a471af3c5681ca58ca3268ad4512ee80abb9cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421548"
---
# <a name="testing-the-odbc-connection"></a>Тестирование подключения ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 При устранении неполадок доступа ODBC к серверам Oracle 7. x и Oracle8 РСУБД может потребоваться проверить правильность установки базовых адаптеров протокола SQL * NET и Oracle. Для этого используйте предоставляемую Oracle служебную Nettest.exe в каталоге Оравин\бин.  
  
 Неттест — это простая программа, которая пытается войти на выбранный сервер, используя только установленное программное обеспечение SQL * NET, которое является частью клиента Oracle. Программа запросит имя входа, пароль и строку подключения TNS. Если клиент Oracle установлен правильно, программа просто выведет сообщение PING успешно. Если имя входа не прошло успешно, необходимо обратиться к администратору базы данных.
