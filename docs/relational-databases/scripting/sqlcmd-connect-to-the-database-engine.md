---
title: "Подключение к ядру СУБД при помощи программы sqlcmd | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sqlcmd utility, Database Engine connections
- Named Pipes [SQL Server], sqlcmd utility
- TCP/IP [SQL Server], client protocols
- network protocols [SQL Server], sqlcmd utility
- protocols [SQL Server], sqlcmd utility
- VIA
- client protocols [SQL Server]
ms.assetid: 74b0fb71-7f8e-4171-9431-d07528532524
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cccbf7d6ae6b1b999ab3f08eff2aee1771293c7f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sqlcmd---connect-to-the-database-engine"></a>sqlcmd — подключение к ядру СУБД
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает клиентское подключение при помощи сетевого протокола TCP/IP (по умолчанию) и протокола именованных каналов. Может также использоваться протокол общей памяти, если клиент устанавливает соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на том же компьютере. Существуют три наиболее часто используемых способа для выбора протокола. Протокол, используемый служебной программой **sqlcmd** , определяется в следующем порядке:  
  
-   Служебная программа**sqlcmd** использует протокол, который указан в составе строки подключения, как показано ниже.  
  
-   Если в строке подключения не указан протокол, программа **sqlcmd** использует протокол, определенный как часть псевдонима, к которому выполняется подключение. Инструкции по настройке **sqlcmd** для использования определенного сетевого протокола при помощи создания псевдонима см. в статье [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md).  
  
-   Если протокол не задается каким-либо иным образом, программа **sqlcmd** использует сетевой протокол, определяемый порядком протоколов в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В следующих примерах демонстрируются различные способы соединения с экземпляром по умолчанию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] через порт 1433 и с именованными экземплярами компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , которые прослушивают порт 1691. В некоторых этих примерах используется IP-адрес адаптера замыкания на себя (127.0.0.1). Проведите проверку при помощи IP-адреса сетевой интерфейсной платы компьютера.  
  
 Подключение к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] с заданием имени экземпляра:  
  
```  
sqlcmd -S ComputerA  
sqlcmd -S ComputerA\instanceB  
```  
  
 Подключение к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] с указанием IP-адреса:  
  
```  
sqlcmd -S 127.0.0.1  
sqlcmd -S 127.0.0.1\instanceB  
```  
  
 Подключение к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] с указанием порта TCP/IP:  
  
```  
sqlcmd -S ComputerA,1433  
sqlcmd -S ComputerA,1691  
sqlcmd -S 127.0.0.1,1433  
sqlcmd -S 127.0.0.1,1691  
```  
  
### <a name="to-connect-using-tcpip"></a>Подключение по протоколу TCP/IP  
  
-   Подключение производится с помощью следующего общего синтаксиса:  
  
    ```  
    sqlcmd -S tcp:<computer name>,<port number>  
    ```  
  
-   Подключение к экземпляру по умолчанию:  
  
    ```  
    sqlcmd -S tcp:ComputerA,1433  
    sqlcmd -S tcp:127.0.0.1,1433  
    ```  
  
-   Подключение к именованному экземпляру:  
  
    ```  
    sqlcmd -S tcp:ComputerA,1691  
    sqlcmd -S tcp:127.0.0.1,1691  
    ```  
  
### <a name="to-connect-using-named-pipes"></a>Подключение через именованные каналы  
  
-   Подключитесь, используя один из следующих вариантов синтаксиса:  
  
    ```  
    sqlcmd -S np:\\<computer name>\<pipe name>  
    ```  
  
-   Подключение к экземпляру по умолчанию:  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\sql\query  
    ```  
  
-   Подключение к именованному экземпляру:  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\MSSQL$<instancename>\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\MSSQL$<instancename>\sql\query  
    ```  
  
### <a name="to-connect-using-shared-memory-a-local-procedure-call-from-a-client-on-the-server"></a>Подключение через общую память (вызов локальной процедуры) из клиента на сервере  
  
-   Подключитесь, используя один из следующих вариантов синтаксиса:  
  
    ```  
    sqlcmd -S lpc:<computer name>  
    ```  
  
-   Подключение к экземпляру по умолчанию:  
  
    ```  
    sqlcmd -S lpc:ComputerA  
    ```  
  
-   Подключение к именованному экземпляру:  
  
    ```  
    sqlcmd -S lpc:ComputerA\<instancename>  
    ```  
  
  
