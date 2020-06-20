---
title: 'Средство управления командной строки: SqlLocalDB.exe | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 147afb38ae7d4ca81d07784aff4efeb28a0859a8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050998"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>Программа командной строки: SqlLocalDB.exe
  Программа SqlLocalDB.exe — это простое средство для управления экземплярами LocalDB из командной строки. Оно реализовано как простая оболочка для API экземпляра LocalDB. Как и во многих аналогичных средствах SQL Server (например, SQLCMD), параметры передаются в SqlLocalDB как параметры командной строки, а вывод отправляется на консоль.  
  
 Программа SqlLocalDB позволяет разработчикам использовать LocalDB без необходимости писать код для вызова API или использования других средств для этой цели.  
  
## <a name="sqllocaldb-options"></a>Параметры программы SqlLocalDB  
 SqlLocalDB поддерживает следующие параметры.  
  
|Параметр|Действие|  
|------------|------------------|  
|`-?`|Выводит текст справки.|  
|`create&#124;c "instance name" [version-number] [-s]`|Создает новый экземпляр LocalDB с заданным именем и версией.<br /><br /> Если параметр [version-number] опущен, используется значение по умолчанию — версия сборки SqlLocalDB.<br /><br /> -s запускает новый экземпляр LocalDB после его создания.|  
|`delete&#124;d "instance name"`|Удаляет экземпляр LocalDB с заданным именем.|  
|`start&#124;s "instance name"`|Запускает экземпляр LocalDB с заданным именем.|  
|`stop&#124;p "instance name" [-i&#124;-k]`|Останавливает экземпляр LocalDB с заданным именем после завершения выполнения текущих запросов.<br /><br /> -i запрашивает завершение работы экземпляра LocalDB с параметром NOWAIT.<br /><br /> -k прерывает процесс экземпляра LocalDB, не связываясь с ним.|  
|`share&#124;h ["owner SID or account"] "private name" "shared name"`|Делает указанный частный экземпляр общим, используя указанное общее имя. Если идентификатор безопасности пользователя или имя учетной записи не указаны, используется значение по умолчанию — имя текущего пользователя.|  
|`unshare&#124;u "shared name"`|Выводит из совместного использования указанный общий экземпляр LocalDB.|  
|`info&#124;i`|Перечисляет все существующие экземпляры LocalDB, принадлежащие текущему пользователю, и все общие экземпляры LocalDB.|  
|`info&#124;i "instance name"`|Выводит сведения об указанном экземпляре LocalDB.|  
|`versions&#124;v`|Перечисляет все версии LocalDB, установленные на компьютере.|  
|||  
|`trace&#124;t on&#124;off`|Включает или отключает трассировку.|  
  
 Программа SqlLocalDB рассматривает пробелы как разделители; имена экземпляров, которые содержат пробелы и специальные символы, необходимо заключать в кавычки. Пример:  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
