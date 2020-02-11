---
title: Установка помощника по обновлению из командной строки | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b694af5b760ae3c1ead1e4984c35ef61c0fa602
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094339"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a>Установка помощника по обновлению из командной строки
  Установить помощник по обновлению можно как с помощью мастера установки, так и из командной строки. С помощью командной строки можно производить установку в автоматическом режиме.  
  
## <a name="installation-syntax"></a>Синтаксис установки  
 Основной синтаксис установки помощника по обновлению из командной строки выглядит следующим образом:  
  
 `SQLUA.msi [options]`  
  
 В следующей таблице приведены наиболее часто применяемые параметры.  
  
|Аргумент|Description|  
|--------------|-----------------|  
|/q [n&#124;b&#124;r&#124;f]|Задает уровень пользовательского интерфейса (UI):<br /><br /> n = без интерфейса<br /><br /> b = базовый интерфейс (только ход выполнения, без подсказок)<br /><br /> r = сокращенный интерфейс (диалоговое окно в конце установки)<br /><br /> f = полный интерфейс|  
|/L|Определяет параметры файла журнала. Чтобы записывать все сообщения в *log_file_name*, используйте **-L\*v**_log_file_name_. Чтобы регистрировать только сообщения об ошибках `-Le`, используйте *log_file_name*.|  
|ADDLOCAL = ALL&#124; REMOVE = ALL&#124;REINSTALL = ALL|Определяет, нужно ли установить (ADDLOCAL), удалить (REMOVE) или переустановить (REINSTALL) помощник по обновлению.|  
|UAINSTALLDIR=path|Устанавливает помощник по обновлению в местоположение, указанное в параметре path.|  
  
## <a name="installation-examples"></a>Примеры установки  
 В следующих примерах показано, как установить помощник по обновлению с помощью командной строки.  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 При запуске этой команды можно также использовать программу Msiexec.  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 Это может оказаться полезным, если есть необходимость в дополнительных параметрах установки.  
  
## <a name="removal-examples"></a>Примеры удаления  
 В следующих примерах показано, как удалить помощник по обновлению с помощью командной строки.  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 При запуске этой команды можно также использовать программу Msiexec.  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a>См. также:  
 [Установка помощника по обновлению](../../../2014/sql-server/install/installing-upgrade-advisor.md)   
 [Компоненты, необходимые для помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
