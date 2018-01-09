---
title: "Программа командной строки: SqlLocalDB.exe | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apilocation: sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6ffc8033651fedbe906086f0a35ef31d463f6e31
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>Программа командной строки SqlLocalDB.exe
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]SqlLocalDB.exe — это простое средство, которое дает пользователю возможность управления экземплярами LocalDB из командной строки. Оно реализовано как простая оболочка для API экземпляра LocalDB. Как и во многих аналогичных средствах SQL Server (например, SQLCMD), параметры передаются в SqlLocalDB как параметры командной строки, а вывод отправляется на консоль.  
  
 Программа SqlLocalDB позволяет разработчикам использовать LocalDB без необходимости писать код для вызова API или использования других средств для этой цели.  
  
## <a name="sqllocaldb-options"></a>Параметры программы SqlLocalDB  
 SqlLocalDB поддерживает следующие параметры.  
  
|Параметр|Действие|  
|------------|------------------|  
|`-?`|Выводит текст справки.|  
|"create\|«Имя экземпляра» c [номер версии] [-s] "|Создает новый экземпляр LocalDB с заданным именем и версией.<br /><br /> Если параметр [version-number] опущен, используется значение по умолчанию — версия сборки SqlLocalDB.<br /><br /> -s запускает новый экземпляр LocalDB после его создания.|  
|"delete\|«Имя экземпляра» d "|Удаляет экземпляр LocalDB с заданным именем.|  
|"сценарий|«Имя экземпляра» s "|Запускает экземпляр LocalDB с заданным именем.|  
|"stop\|p «имя экземпляра» [-i\|-k] "|Останавливает экземпляр LocalDB с заданным именем после завершения выполнения текущих запросов.<br /><br /> -i запрашивает завершение работы экземпляра LocalDB с параметром NOWAIT.<br /><br /> -k прерывает процесс экземпляра LocalDB, не связываясь с ним.|  
|"share\|h [«ИД безопасности владельца или учетной записи»] «закрытое имя» «общее имя» "|Делает указанный частный экземпляр общим, используя указанное общее имя. Если идентификатор безопасности пользователя или имя учетной записи не указаны, используется значение по умолчанию — имя текущего пользователя.|  
|"unshare\|u «общее имя» "|Выводит из совместного использования указанный общий экземпляр LocalDB.|  
|"info\|я "|Перечисляет все существующие экземпляры LocalDB, принадлежащие текущему пользователю, и все общие экземпляры LocalDB.|  
|"info\|«Имя экземпляра» i "|Выводит сведения об указанном экземпляре LocalDB.|  
|"versions\|v "|Перечисляет все версии LocalDB, установленные на компьютере.|  
|||  
|"trace\|t on\|Отключение "|Включает или отключает трассировку.|  
  
 Программа SqlLocalDB рассматривает пробелы как разделители; имена экземпляров, которые содержат пробелы и специальные символы, необходимо заключать в кавычки. Пример:  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
