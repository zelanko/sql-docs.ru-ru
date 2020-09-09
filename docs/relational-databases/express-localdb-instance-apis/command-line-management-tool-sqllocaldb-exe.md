---
description: 'Программа командной строки: SqlLocalDB.exe'
title: 'Средство управления командной строки: SqlLocalDB.exe | Документация Майкрософт'
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apilocation:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4b2140dc74bd9e30bb4c707681aa9b491f8ea272
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548902"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>Программа командной строки: SqlLocalDB.exe
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Программа SqlLocalDB.exe — это простое средство для управления экземплярами LocalDB из командной строки. Оно реализовано как простая оболочка для API экземпляра LocalDB. Как и во многих аналогичных средствах SQL Server (например, SQLCMD), параметры передаются в SqlLocalDB как параметры командной строки, а вывод отправляется на консоль.  
  
 Программа SqlLocalDB позволяет разработчикам использовать LocalDB без необходимости писать код для вызова API или использования других средств для этой цели.  
  
## <a name="sqllocaldb-options"></a>Параметры программы SqlLocalDB  
 SqlLocalDB поддерживает следующие параметры.  
  
|Параметр|Действие|  
|------------|------------------|  
|`-?`|Выводит текст справки.|  
|`create\|c "instance name" [version-number] [-s]`|Создает новый экземпляр LocalDB с заданным именем и версией.<br /><br /> Если параметр [version-number] опущен, используется значение по умолчанию — версия сборки SqlLocalDB.<br /><br /> -s запускает новый экземпляр LocalDB после его создания.|  
|`delete\|d "instance name"`|Удаляет экземпляр LocalDB с заданным именем.|  
|`start\|s "instance name"`|Запускает экземпляр LocalDB с заданным именем.|  
|`stop\|p "instance name" [-i\|-k]`|Останавливает экземпляр LocalDB с заданным именем после завершения выполнения текущих запросов.<br /><br /> -i запрашивает завершение работы экземпляра LocalDB с параметром NOWAIT.<br /><br /> -k прерывает процесс экземпляра LocalDB, не связываясь с ним.|  
|`share\|h ["owner SID or account"] "private name" "shared name"`|Делает указанный частный экземпляр общим, используя указанное общее имя. Если идентификатор безопасности пользователя или имя учетной записи не указаны, используется значение по умолчанию — имя текущего пользователя.|  
|`unshare\|u "shared name"`|Выводит из совместного использования указанный общий экземпляр LocalDB.|  
|`info\|i`|Перечисляет все существующие экземпляры LocalDB, принадлежащие текущему пользователю, и все общие экземпляры LocalDB.|  
|`info\|i "instance name"`|Выводит сведения об указанном экземпляре LocalDB.|  
|`versions\|v`|Перечисляет все версии LocalDB, установленные на компьютере.|  
|||  
|`trace\|t on\|off`|Включает или отключает трассировку.|  
  
 Программа SqlLocalDB рассматривает пробелы как разделители; имена экземпляров, которые содержат пробелы и специальные символы, необходимо заключать в кавычки. Пример:  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
