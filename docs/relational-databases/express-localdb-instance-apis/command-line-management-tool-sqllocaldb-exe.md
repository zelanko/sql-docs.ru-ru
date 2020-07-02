---
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c39272a1f8af7fce092f7aa31ac3a4f7ebd2263
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765256"
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
  
  
